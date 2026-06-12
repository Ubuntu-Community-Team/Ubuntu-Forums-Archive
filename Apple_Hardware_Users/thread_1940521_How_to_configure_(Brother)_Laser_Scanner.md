---
title: "How to configure (Brother) Laser Scanner"
date: 2012-03-13
forum: Apple Hardware Users
---

### Post by Viraj Rao on 2012-03-13
Am new to Ubuntu  and have it installed v11.10 it on my Mac using VirtualBox 4.1.8. Am currently facing an issue, wherein am able to print the documents but not scan the documents. Am using Brother Printer model DCP-7030. Till date I have performed following actions, to make my scanner working.

Step 1

cd Desktop

sudo dpkg -i <<scanner driver>>.deb

sudo gedit /etc/udev/rules.d/45-libsane.rules

# Brother DCP-115C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"

sudo lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 003: ID 04f9:01ea Brother Industries, Ltd 

sudo chmod a+w /dev/bus/usb/001/003 


Step 2

Tried to add user to vboxusergroup using following command
sudo usermod -a -G vboxusers viraj

Received following message
usermod: group 'vboxusers' does not exist


Am trying to fix this scanner issue for last 10 days. Any workingsolution, is highly appreciated.

---

