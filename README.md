# EmployeePortal - Azure DevOps CI Pipeline

## 📌 Project Overview

This project demonstrates a Continuous Integration (CI) pipeline for an ASP.NET Core application.

The application code is stored in GitHub, and Azure DevOps is used to automatically restore and build the application whenever changes are pushed to the `master` branch.

## 🏗️ Architecture

Developer → GitHub → Azure DevOps Pipeline → Self-Hosted Agent → Windows Server VM → .NET Build

## 🛠️ Technologies Used

- ASP.NET Core
- .NET
- Git
- GitHub
- Azure DevOps
- Azure Virtual Machine
- Windows Server
- Azure DevOps Self-Hosted Agent
- YAML

## 🔄 CI Pipeline Flow

1. Developer makes changes to the ASP.NET Core project.
2. Code is pushed to the GitHub `master` branch.
3. Azure DevOps automatically triggers the CI pipeline.
4. The pipeline uses the self-hosted agent.
5. The agent runs on a Windows Server VM.
6. `dotnet restore` restores project dependencies.
7. `dotnet build` builds the application.
8. The pipeline reports the build result.

## 📄 Pipeline Configuration

The pipeline is defined in `azure-pipelines.yml`.

```yaml
trigger:
- master

pool:
  name: Default

variables:
  buildConfiguration: 'Release'

steps:
- script: dotnet restore
  displayName: 'Restore project'

- script: dotnet build --configuration $(buildConfiguration) --no-restore
  displayName: 'Build project'