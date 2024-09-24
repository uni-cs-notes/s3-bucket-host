
# Abu Fatima Zohra Travel and Tours S3 Upload Documentation

## Introduction
This document outlines the steps to configure AWS CLI and upload files and folders to an S3 bucket, specifically to the bucket `abufatimatuzahratravelandtour.com`.

### Prerequisites
Before starting, ensure you have the following:
- **AWS Access Key ID** and **Secret Access Key**
- **AWS CLI installed**
- **S3 bucket name** (`abufatimatuzahratravelandtour.com`)

## Step-by-Step Guide

### 1. Install AWS CLI
If the AWS CLI is not already installed, follow these steps:

- For Linux/MacOS:
  ```bash
  curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
  sudo installer -pkg AWSCLIV2.pkg -target /
  ```

- For Windows, download the AWS CLI MSI installer from [AWS Documentation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

To verify installation:
```bash
aws --version
```

### 2. Configure AWS CLI
Once AWS CLI is installed, configure it using your provided **AWS Access Key ID** and **Secret Access Key**:

```bash
aws configure
```

You will be prompted to enter:
- **AWS Access Key ID**: Enter the access key provided.
- **AWS Secret Access Key**: Enter the secret key provided.
- **Default region name**: Enter the region where your bucket is located (e.g., `us-east-1`).
- **Default output format**: Enter `json` (default format).

### 3. Verify the AWS Configuration
After configuring, you can verify the AWS credentials by running:

```bash
aws sts get-caller-identity
```

This command returns the account information and confirms the AWS CLI is configured correctly.

### 4. Uploading Files and Folders to S3 Bucket

To upload individual files or entire folders to the S3 bucket `abufatimatuzahratravelandtour.com`, follow these steps.

#### a. Upload a Single File
Use the following command to upload a single file to the bucket:

```bash
aws s3 cp /path/to/your/file.txt s3://abufatimatuzahratravelandtour.com/
```

#### b. Upload an Entire Folder
To upload a folder with multiple files recursively to the S3 bucket:

```bash
aws s3 cp /home/qazifaisal/Desktop/abu-fatima-zohra s3://abufatimatuzahratravelandtour.com/ --recursive
```
This will upload the folder `/abu-fatima-zohra` and all of its contents to the S3 bucket.

### 5. Verify Upload
You can list the contents of the bucket to ensure your files have been successfully uploaded:

```bash
aws s3 ls s3://abufatimatuzahratravelandtour.com/
```

### 6. Error Handling
If you encounter errors during the upload, common issues might include:
- Incorrect **bucket name**
- Missing **permissions** (ensure your AWS credentials allow `s3:PutObject` actions).
- Region mismatch: Ensure you are operating in the correct region. If not set correctly during configuration, you can add the region flag in commands like so:
  ```bash
  aws s3 cp /home/qazifaisal/Desktop/abu-fatima-zohra s3://abufatimatuzahratravelandtour.com/ --recursive --region us-east-1
  ```

### 7. Additional Commands
- **Download a File**:
  ```bash
  aws s3 cp s3://abufatimatuzahratravelandtour.com/file.txt /local/path/file.txt
  ```
  
- **Delete a File from the Bucket**:
  ```bash
  aws s3 rm s3://abufatimatuzahratravelandtour.com/file.txt
  ```

---

## Conclusion
This documentation provides a guide to configuring the AWS CLI and uploading files and folders to your S3 bucket. If you have additional questions or run into issues, feel free to reach out.
