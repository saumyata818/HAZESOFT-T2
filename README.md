# HAZESOFT-T2 - Automated Deployment of Task 1 using Ansible

## Overview

In Task 2, the goal was to **automate the deployment of Task 1 (HAZESOFT-T1)** using Ansible.  
Instead of manually copying files and setting up Nginx, I created an **Ansible playbook** that performs all deployment steps automatically on an Ubuntu environment (WSL or VM).  

Once deployed, visiting `http://localhost/index.html` displays the message:

You did it, Congratulations!!


## What I Did in Task 2

1. **Created a public GitHub repository** `HAZESOFT-T2`.
2. **Set up an Ansible inventory file** (`inventory.ini`) to define the target host:
   - For WSL/local deployment, the host is `localhost`.
   - For VM deployment, it can be replaced with the VM’s IP and SSH credentials.
3. **Developed an Ansible playbook** (`playbook.yml`) that:
   - Updates the apt package index
   - Installs required packages (`nginx` and `git`)
   - Clones the Task 1 repository (`HAZESOFT-T1`)
   - Copies the `site/` folder from Task 1 to Ubuntu Nginx’s default web root (`/var/www/html/`)
   - Ensures Nginx is started and enabled
4. **Created the `site/index.html` file** in the Task 1 repo to display the success message.
5. **Tested the deployment** using `curl` to verify that the website loads correctly.



## Repository Structure

HAZESOFT-T2/
├── inventory.ini # Defines the target host for Ansible
├── playbook.yml # Ansible playbook to deploy Task 1 automatically
└── site/
└── index.html # HTML file to display "You did it, Congratulations!!"




## Prerequisites

- Ubuntu system (WSL, VM, or physical machine)
- Ansible installed
sudo apt update
sudo apt install ansible -y
Internet connection to clone GitHub repositories

How to Run Task 2
Clone the repository:


git clone https://github.com/<your-username>/HAZESOFT-T2.git
cd HAZESOFT-T2
Ensure the site files exist:

<!-- site/index.html -->
<h1>You did it, Congratulations!!</h1>
Run the Ansible playbook:


ansible-playbook -i inventory.ini playbook.yml
Verify deployment:


curl http://localhost/index.html
Expected output:


You did it, Congratulations!!


Notes
Ubuntu’s default Nginx web root is /var/www/html/.
The playbook is idempotent — running it multiple times will not break the setup.
If using a VM, ensure SSH is enabled and reachable from your host machine.
All commands in the playbook are run as root using become: yes.


Author
Saumyata Nepal
