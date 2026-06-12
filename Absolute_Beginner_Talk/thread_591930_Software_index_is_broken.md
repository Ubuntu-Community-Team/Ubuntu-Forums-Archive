---
title: "Software index is broken"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Kalur on 2007-10-25
I get a "Software Index is broken" message box when I try to update Ubuntu.  The message box says

 'It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.'

Synaptic will not work when I try it and when I run "sudo apt-get install -f" I get the following message.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-2.6.20-15
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 58.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140475 files and directories currently installed.)
Removing linux-headers-2.6.20-15 ...
dpkg: error processing linux-headers-2.6.20-15 (--remove):
 cannot remove file `/usr/src/linux-headers-2.6.20-15/arch/powerpc/kernel/Makefile': Not a directory
Errors were encountered while processing:
 linux-headers-2.6.20-15
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be much appreciated.

---

### Post by caffienefree on 2007-10-25
Try executing:

dpkg --configure -a

---

### Post by Kalur on 2007-10-26
I'm fairly new to Ubuntu.  I can't seem to get dkpg --configure -a to work.  When I write it into the terminal is says I need superuser privileges.  When I put the sudo command in before it I get no response.  What am I doing wrong?

---

### Post by Anicka on 2007-10-26
This you can try: ```
sudo dpkg -P --force-remove-reinstreq linux-headers-2.6.20-15
```

It will with force remove the package.

---

### Post by Kalur on 2007-10-26
Still no luck.  I get this error message when I try to remove the package following Anicka's reply.

(Reading database ... 140475 files and directories currently installed.)
Removing linux-headers-2.6.20-15 ...
dpkg: error processing linux-headers-2.6.20-15 (--purge):
 cannot remove file `/usr/src/linux-headers-2.6.20-15/arch/powerpc/kernel/Makefile': Not a directory
Errors were encountered while processing:
 linux-headers-2.6.20-15

More help needed :(

---

### Post by Kalur on 2007-10-26
bump!

This seems to be a common error that I'm having:
cannot remove file `/usr/src/linux-headers-2.6.20-15/arch/powerpc/kernel/Makefile': Not a directory

---

### Post by Kalur on 2007-10-26
Still need help, can't seem to find an answer to what is going on.

---

### Post by zvacet on 2007-10-27
```
sudo apt-get remove --purge  linux-headers-2.6.20-15
```

or **synaptic<edit>fix broken package**

---

### Post by Kalur on 2007-10-27
No luck Zvacet :(  I get this error message:

dpkg: error processing linux-headers-2.6.20-15 (--remove):
 cannot remove file `/usr/src/linux-headers-2.6.20-15/arch/powerpc/kernel/Makefile': Not a directory
Errors were encountered while processing:
 linux-headers-2.6.20-15
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is there a directory missing? corrupted?

---

