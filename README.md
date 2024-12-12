# system_info.sh

echo "# system_info.sh" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/shed-tech-Ops/system_info.sh.git
git push -u origin main

#!/bin/bash

# System Info Script
# Author: [Your Name]
# Date: $(date)
# Description: This script displays basic system information.

# Check if the script is being run as root
if [ "$EUID" -ne 0 ]; then
  echo "Please run as root to gather complete system info."
  exit 1
fi

echo "-----------------------------------------"
echo " SYSTEM INFORMATION REPORT "
echo "-----------------------------------------"
echo ""

# Hostname
echo "Hostname: $(hostname)"

# OS and Kernel
echo "Operating System: $(cat /etc/redhat-release)"
echo "Kernel Version: $(uname -r)"

# Uptime
echo "System Uptime: $(uptime -p)"

# Logged-in Users
echo "Currently Logged-in Users:"
who

# Memory Usage
echo "Memory Usage:"
free -h

# Disk Usage
echo "Disk Usage:"
df -h

# Network Configuration
echo "Network Configuration:"
ip a

# Active Services
echo "Active Services:"
systemctl list-units --type=service --state=active

echo "-----------------------------------------"
echo " END OF SYSTEM INFORMATION "
echo "-----------------------------------------"
