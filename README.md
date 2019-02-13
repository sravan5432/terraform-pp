# TerraformProject

What project does:

1. it sets autoscaling group with ubuntu OS
2. we don't have to mention amazon AMI , code will search automatically latest ubuntu 14.04 OS through filters.
3. It searchs availability zone by itself and spreads EC2 across the zone to have high availability.
4. Make sure "min_size " with in "terraform.tfsvars" file is equal to the number of availablity zones on the region.
5. Every EC2 which is part of the Autoscaling group will by default has docker engine, nginx and postgresql-client installed.
6. once the every thing is up, use the below command to connect to postgres RDS instance from EC2 instance created.
      i) psql \
   --host="INSTANCE END POINT WITHOUT PORT NUMBER" \
   --port=5432 \
   --username pavan \
   --password \
   --dbname=pavandb

Example: 

psql \
   --host=pavandb.cpjv6dd5xtyl.eu-west-2.rds.amazonaws.com \
   --port=5432 \
   --username pavan \
   --password \
   --dbname=pavandb


How to Run:

1. Save files on the disk.
2. update the terraform.tfvars with required values. ( stack name, access key, secret key , db username and db password)
3. makes sure you have terraform in your system/server.
4. execute sequence of steps below.


Provisioning:

   i)    terraform validate   (makes sure you don't have any errors in the code)
   ii)   terraform init ( initialization )
   iii)  terraform plan -out "<name>"
   iv)   terraform apply "<name>"
   
   Now the magic, Login into your account and check you should have resources created...!!!
   
Deprovisioning:

i) terraform destroy - will remove all the resources provisioned with terraform apply.
