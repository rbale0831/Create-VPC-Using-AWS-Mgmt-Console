rohit-vpc# Design AWS VPC using AWS Management Console

## Step-01: Introduction
- Create VPC
- Create Public and Private Subnets
- Create Internet Gateway and Associate to VPC
- Create NAT Gateway in Public Subnet
- Create Public Route Table, Add Public Route via Internet Gateway and Associate Public Subnet
- Create Private Route Table, Add Private Route via NAT Gateway and Associate Private Subnet

<img width="1091" height="561" alt="image" src="https://github.com/user-attachments/assets/9c8d5d03-7555-4b09-93ee-a7a6999480e0" />


## Step-02: Create VPC
- **Name:** rohit-vpc
- **IPv4 CIDR Block:** 10.0.0.0/16
- Rest all defaults
- Click on **Create VPC**

<img width="1091" height="526" alt="image" src="https://github.com/user-attachments/assets/953c8055-61c3-40f1-871f-5904781d80ef" />

<img width="1091" height="538" alt="image" src="https://github.com/user-attachments/assets/8395b0cb-0e9b-47ce-bf1f-b330f928685a" />



## Step-03: Create Subnets
### Step-03-01: Public Subnet
- **VPC ID:** rohit-vpc
- **Subnet Name::** rohit-public-subnet-1
- **Availability zone:** us-east-1a
- **IPv4 CIDR Block:** 10.0.1.0/24

<img width="1091" height="446" alt="image" src="https://github.com/user-attachments/assets/bc774624-a9b6-427c-8430-3104116bf919" />

<img width="1091" height="538" alt="image" src="https://github.com/user-attachments/assets/cf8a4a61-78c5-4caa-809d-cd5840df13d0" />


### Step-03-02: Private Subnet
- **Subnet Name::** rohit-private-subnet-1
- **Availability zone:** us-east-1a
- **IPv4 CIDR Block:** 10.0.101.0/24
- Click on **Create Subnet**

<img width="1091" height="538" alt="image" src="https://github.com/user-attachments/assets/62b512fa-ec82-45c9-b5be-dc8ae43dc0be" />

<img width="1091" height="538" alt="image" src="https://github.com/user-attachments/assets/c4cdfdfa-1f42-4944-9c6b-40527f7fecaf" />

## Step-04: Create Internet Gateway and Associate it to VPC
- **Name Tag:** rohit-igw
- Click on **Create Internet Gateway**
- Click on Actions -> Attach to VPC -> rohit-vpc

<img width="1091" height="538" alt="image" src="https://github.com/user-attachments/assets/be10f390-6de9-4bbe-945a-5a2d0e632ab9" />

<img width="1091" height="538" alt="image" src="https://github.com/user-attachments/assets/d3c14fbd-1654-42d1-948a-0cc42361e24c" />

<img width="1091" height="442" alt="image" src="https://github.com/user-attachments/assets/6cf616e9-4d50-488d-b2c0-46280bb44fc9" />

<img width="1091" height="469" alt="image" src="https://github.com/user-attachments/assets/51fac605-f8b2-4de8-a3a3-cf1482577cd0" />

<img width="1091" height="358" alt="image" src="https://github.com/user-attachments/assets/0dc3ac8f-baab-45c1-aa79-0e32d455d654" />



## Step-05: Create NAT Gateway
- **Name:** rohit-nat-gateway
- **Subnet:** rohit-public-subnet-1
- **Availability mode:** Zonal
- **Allocate Elastic Ip:** click on that
- Click on **Create NAT Gateway**

<img width="1091" height="492" alt="image" src="https://github.com/user-attachments/assets/4beb7f4f-5775-401a-a8b6-c12694e8262b" />


## Step-06: Create Public Route Table and Create Routes and Associate Subnets
### Step-06-01: Create Public Route Table
- **Name tag:** rohit-public-route-table
- **vpc:** rohit-vpc
- Click on **Create**

<img width="1091" height="389" alt="image" src="https://github.com/user-attachments/assets/d66d5627-a5ea-45bd-ae6d-78aa3587c3c0" />
<img width="1091" height="380" alt="image" src="https://github.com/user-attachments/assets/e2ad2a17-f2d1-40d2-9e38-f7dbae2daa90" />



### Step-06-02: Create Public Route in newly created Route Table
- Click on **Add Route**
- **Destination:** 0.0.0.0/0
- **Target:** rohit-igw
- Click on **Save Route**

<img width="1091" height="311" alt="image" src="https://github.com/user-attachments/assets/478a26d0-a0e7-4b47-a176-42f69826fb0f" />


### Step-06-03: Associate Public Subnet 1 in Route Table
- Click on **Edit Subnet Associations**
- Select **rohit-public-subnet-1**
- Click on **Save**

<img width="1091" height="408" alt="image" src="https://github.com/user-attachments/assets/a5908d46-6b3a-4e72-8e23-66aba305a5e4" />

<img width="1091" height="314" alt="image" src="https://github.com/user-attachments/assets/9078df5c-00c0-41a6-a044-b0425de77ef8" />

<img width="1091" height="318" alt="image" src="https://github.com/user-attachments/assets/45d0aee5-87f3-4da0-bc97-5d9cbeb5b7eb" />

<img width="1091" height="428" alt="image" src="https://github.com/user-attachments/assets/5530bba8-b9b7-41ad-a167-ca268971fc40" />


## Step-07: Create Private Route Table and Create Routes and Associate Subnets
### Step-07-01: Create Private Route Table
- **Name tag:** rohit-private-route-table
- **vpc:** rohit-vpc
- Click on **Create**

<img width="1091" height="401" alt="image" src="https://github.com/user-attachments/assets/a495e930-c5e7-4ebf-ab07-a124c9528b97" />

<img width="1091" height="335" alt="image" src="https://github.com/user-attachments/assets/e7b97468-7b96-4b43-899e-8645aa8ae1d1" />


### Step-07-02: Create Private Route in newly created Route Table
- Click on **Add Route**
- **Destination:** 0.0.0.0/0
- **Target:** rohit-nat-gateway
- Click on **Save Route**

<img width="1091" height="273" alt="image" src="https://github.com/user-attachments/assets/6fdc2bd7-5c30-4a0c-989d-ff6d9fdb2e53" />
<img width="1091" height="428" alt="image" src="https://github.com/user-attachments/assets/5aee9e48-63e5-442d-817c-7babb6693609" />

### Step-07-03: Associate Private Subnet 1 in Route Table
- Click on **Edit Subnet Associations**
- Select **rohit-private-subnet-1**
- Click on **Save**

<img width="1091" height="314" alt="image" src="https://github.com/user-attachments/assets/49e62592-6811-4348-8a3a-b25763e86326" />

<img width="1091" height="378" alt="image" src="https://github.com/user-attachments/assets/9f0200a5-1ca7-4df1-aa24-49ae57476f6b" />




## Step-08: Clean-Up
- Delete `rohit-nat-gateway`
- Wait till NAT Gateway is deleted
- Delete `rohit-vpc`




