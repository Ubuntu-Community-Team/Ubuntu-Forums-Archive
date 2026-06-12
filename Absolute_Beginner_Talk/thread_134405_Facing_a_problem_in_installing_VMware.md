---
title: "Facing a problem in installing VMware"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by Beliuntu on 2006-02-21
I am a new user and i faced a problem in installing virtual machine 

I have installed Virtual Machine by the following steps :

1-Used alien to convert the *.rpm file to *.deb file .
2-I installed the *.deb file .
3-Then used the command "vmware" in the terminal it give me the following error

/usr/bin/vmware: line 85: /etc/vmware/locations: No such file or directory
/usr/bin/vmware: line 183: /lib/wrapper-gtk24.sh: No such file or directory
/usr/bin/vmware: line 183: exec: /lib/wrapper-gtk24.sh: cannot execute: No such file or directory

Thanx.........

---

### Post by najames on 2006-02-21
Get the tar version, run the simple command to untar it.  Follow the instructions on VMware's website for installing, if using the VMware server, follow the GSX instructions for more information.  Make sure you get the command to apt-get kernel headers, gcc+, etc. Select defaults and say yes to the options presented during the VMware install. 

I am running Ubuntu Dapper 64bit host, VMware Workstation eval, WIn2000 guest, Ubuntu Breezy 32bit guest now.  So far, so good, but I just installed it last night.

---

