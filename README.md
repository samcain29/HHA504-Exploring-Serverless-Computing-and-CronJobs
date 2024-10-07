# HHA504 Assignment: Exploring Serverless Computing and Cron Jobs in Azure, GCP, and GitHub

## 1. Deploying Serverless Functions

### 1.1 Azure Function Deployment

I deployed a basic HTTP-triggered function using Azure Functions. The function responds with "Hello, World" when triggered by an HTTP request.

#### **Steps:**
1. Created a new Function App in the Azure Portal.
2. Selected the "Consumption (Serverless)" plan.
3. Configured an HTTP trigger with the code to return "Hello, World."
4. Deployed and tested the function.

#### **Azure Function Code:**
```python
import logging
import azure.functions as func

def main(req: func.HttpRequest) -> func.HttpResponse:
    logging.info('HTTP trigger function processed a request.')
    return func.HttpResponse("Hello, World!")
```

#### **Screenshot of Azure Function Deployment:**
![image](https://github.com/user-attachments/assets/cbcee8bc-45a3-4ce3-a8a9-118d6faafa63)
![image](https://github.com/user-attachments/assets/e39c957e-ba2a-408f-971a-db77256e2142)


### 1.2 Google Cloud Function Deployment

Similarly, I deployed a basic HTTP-triggered function using Google Cloud Functions.

#### **Steps:**
1. Created a new function in the Google Cloud Console.
2. Chose an HTTP trigger and wrote a simple function to return "Hello, World."
3. Deployed and tested the function.

#### **Google Cloud Function Code:**
```python
def hello_world(request):
    return "Hello, World!"
```

#### **Screenshot of Google Cloud Function Deployment:**
![image](https://github.com/user-attachments/assets/aa82c984-b848-426a-9bb3-a269040fa680)
![image](https://github.com/user-attachments/assets/03223986-c0ea-4a79-9ac9-e3dbfdbd35c0)

---

## 2. Setting Up a Cron Job in GitHub Actions

For the GitHub Actions portion of the assignment, I created a cron job that runs daily at midnight and logs "Scheduled task executed."

### 2.1 GitHub Action Workflow YAML

The workflow was defined in the `.github/workflows/cron-job.yml` file with the following configuration:

```yaml
name: Cron Job Example

on:
  schedule:
    - cron: '0 0 * * *'  # Runs daily at midnight UTC

jobs:
  run-script:
    runs-on: ubuntu-latest
    steps:
    - name: Run a script
      run: echo "Scheduled task executed"
```

### 2.2 Screenshot of Workflow Configuration:
![image](https://github.com/user-attachments/assets/1d003126-9f6a-4775-9ddd-4958990aca0e)

---

## 3. Reflection on Functions as a Service (FaaS)

Functions as a Service (FaaS) simplifies the deployment of small, event-driven functions by eliminating the need to manage servers. Both Azure Functions and Google Cloud Functions provide easy-to-use platforms for deploying functions with minimal infrastructure management.

#### **Benefits:**
- Cost efficiency: Pay only for the compute time used.
- Automatic scaling: Functions scale based on demand.
- Simplified deployment: Focus on writing code without managing infrastructure.

#### **Limitations:**
- Cold starts can introduce latency when functions are not frequently invoked.
- Time limits make them unsuitable for long-running processes.

FaaS is especially useful for microservices, real-time data processing, and scheduled tasks, like cron jobs. Both Azure and GCP offer strong FaaS platforms, each with unique strengths in their respective ecosystems. This assignment provided hands-on experience with serverless computing in Azure and GCP, as well as automating scheduled tasks using GitHub Actions. It demonstrated the flexibility and scalability of FaaS, as well as its suitability for event-driven tasks and automation.
