---
title: "Help installing"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by cingh on 2007-01-06
Hello i need help to install VMware Workstation 5.0.0-13124 for Linux, 
can you give me the exact codes (like sudo) to install as i need it, importantly 

Thank You 
Cingh

---

### Post by kelbizzle on 2007-01-06
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29)

---

### Post by hyper_ch on 2007-01-06
First of all VMWare requires a few things... I don't know about the Workstation Version but the server one does:


sudo apt-get install linux-headers-`uname -r` build-essential xinetd

Then try to run the perl install script, in the command shell navigato the the folder wher you extracted vmware and enter:

```

sudo vmware-install.pl

```

If you get complaints about Compiler then you need to isntall this package als:
sudo apt-get install gcc-3.4

As for the install options for most thing you can just press enter and hence accept the default values... be careful reagrding to the networking options. You want (very likely) to have them enabled.

---

### Post by cingh on 2007-01-06
thank you

cingh

---

