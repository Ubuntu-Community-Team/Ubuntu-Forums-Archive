---
title: "VMWare Workstation"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by markwayne on 2008-02-02
Running VMWare Workstation 6.02 and Ubantu 7.01 but unable to install VMWare tools.

OS seems to be ok but VMWare looks for the Tools installation every start.

When I try to install VMWare Tools, two files are presented one a TAR but I do not know how to proceed from this point.  I have tried to execute some of the files but this is my first shot at any form of Linux or Unix and it appear that I am lost (dam Windows)

Any and all help would be greatly appreciated.

---

### Post by KingWilliam on 2008-02-02
What are you actually trying to do? Windows as host and Ubuntu as Guest or Ubuntu as host and Windows as guest?

If windows is the guest os, installing VMware tools should be piece of cake. In the other case (I don't have expierience with a virtual Ubuntu) you might need to compile VMware tools?
-untar the files
-navigate to the directory where you extracted
-try './configure'
-'make'
-'make install'
(don't forget you need build-essentials for compiling software)

---

### Post by dcstar on 2008-02-03
> **markwayne said:**
> Running VMWare Workstation 6.02 and Ubantu 7.01 but unable to install VMWare tools.

OS seems to be ok but VMWare looks for the Tools installation every start.

When I try to install VMWare Tools, two files are presented one a TAR but I do not know how to proceed from this point.  I have tried to execute some of the files but this is my first shot at any form of Linux or Unix and it appear that I am lost (dam Windows)

Any and all help would be greatly appreciated.

You extract the .tar file to your desktop (right-click it), then open a terminal and:
```
cd Desktop
cd vmware-tools-distrib
sudo ./vmware-install.pl 
```

And just use the defaults for all questions - and then select what screen resolution you want the VM to run in.

You then need to start **vmware-toolbox** at each login by adding that command to System-Preferences-Sessions-Startup Programs

You can delete the vmware-tools-distrib folder once you have successfully installed it.

There is a whole separate Virtualization forum where answers on this issue can be found.

---

