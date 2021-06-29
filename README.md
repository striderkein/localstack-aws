# localstack-for-dkids

## What's this?
mocking S3 for local invoking Lambda Function

## preparation
### need to Install
- aws cli
- Docker
### aws configure
```
% aws configure --profile=YOUR_PROFILE_FOR_TEST
AWS Access Key ID [None]: dummy
AWS Secret Access Key [None]: dummy
Default region name [None]: ap-northeast-1
Default output format [None]: json
```
## How to use
### boot
```
docker-compose up -d
```
### create bucket
```
aws s3 mb s3://YOUR_BUCKET --endpoint-url=http://localhost:4566 --profile=YOUR_PROFILE_FOR_TEST
```
when success, you'll see below
```
make_bucket: YOUR_BUCKET
```
### upload file
```
aws s3 cp YOUR/PATH/TO/FILE s3://YOUR_BUCKET --endpoint-url=http://localhost:4566 --profile=YOUR_PROFILE_FOR_TEST
```
`fsi-xml-bucket` にアップロードする場合
```
aws s3 cp YOUR/PATH/TO/FILE s3://fsi-xml-bucket --endpoint-url=http://localhost:4566 --profile=YOUR_PROFILE_FOR_TEST
```

when success, you'll see below
```
upload: YOUR/PATH/TO/FILE to s3://YOUR_BUCKET/FILE
```
### delete file
```
aws s3 --endpoint-url=http://localhost:4566 rm s3://fsi-xml-bucket/FILE_NEED_TO_DELETE --profile=YOUR_PROFILE_FOR_TEST
```
### check file list
```
aws s3 --endpoint-url=http://localhost:4566 ls s3://fsi-xml-bucket --profile=YOUR_PROFILE_FOR_TEST
```
