---
title: "VMware tools"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by ptosiani on 2006-11-12
Hi, i'm new in this. So, i installed my VMware Workstation 5.5.0 in my windows XP service pack 2. Then, i installed Ubuntu 6.06 dapper drake in the VM with no problem. Finally i tried to install the Vmware tools, i saw the CDROM image on the desktop, i downloaded ALIEN to convert the rpm into dev and installed the packae with no problem, in fact look at this:

paolo@PAOLO:~$ aptitude search vmware
i   vmwaretools                     - VMware Tools
i   xserver-xorg-driver-vmware      - X.Org X server -- VMware display driver


it is installed right? Well, i keep getting the same message, "You dont have vmware tools installed" 

Maybe i need to do something else? 

Help.. ... thanks! :D

---

### Post by PilotJLR on 2006-11-12
After the package is installed, you still need to configure it... as root, run "vmware-config-tools.pl"

[http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html)

---

