# aws-fargate-playground

learn [AWS Fargate](https://aws.amazon.com/fargate/)

```sh
# register task definition
aws ecs register-task-definition --cli-input-json file://./task-definitions/hello-world.json

# run task
aws ecs run-task --task-definition "fargate-001" --launch-type "FARGATE" --network-configuration '{"awsvpcConfiguration": {"subnets": ["subnet-154b7928", "subnet-4700526d", "subnet-6cf9a534", "subnet-af5052d9"],"securityGroups": ["sg-047fbd9524f6e2b5e"],"assignPublicIp": "ENABLED"}}'

# *** NOTE ***
# * "assignPublicIp": "ENABLED" is needed for ecs/fargate to pull image from docker hub
# * "securityGroups": must allow outbund traffic
# * make sure log group is already created
```