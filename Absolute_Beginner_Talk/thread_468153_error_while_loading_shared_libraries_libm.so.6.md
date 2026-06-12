---
title: "error while loading shared libraries: libm.so.6"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2007-06-08
Hey all,
I'm trying to install Maple 10 and when I run the install script I get this message:

```
student@bcockfi-laptop:/mnt/iso$ sudo ./installMaple
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.6014/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```

I've installed sun-java6-bin and sun-java6-jre because I assumed it was a problem with Java but now I'm at a dead end.

---

### Post by tbroderick on 2007-06-08
libc6 is installed, right?

---

### Post by AngryMallard on 2007-06-08
Yes

---

### Post by cody50 on 2007-06-17
i'm having trouble too. the same issue. I had it running before in Dapper, no problems but with feisty I get your same output. perhaps that will shed some light on it, Idk.

---

### Post by mark_sfu on 2007-06-24
I ran into the same issue while installing maple 9.5 for linux on Feisty. However, searching on google, I found this fix for the same problem but for a different program

[http://www.zend.com/support/knowledgebase.php?kbid=184&view_only=1](http://www.zend.com/support/knowledgebase.php?kbid=184&view_only=1)

here are the adpated instructions to make this work for maple:

- copy the cd contents to the hard drive
- go to the directory /Linux/Disk1/InstData/VM or wherever the file LinuxInstaller.bin is located
- then do the following two commands

cp LinuxInstaller.bin LinuxInstaller.bin.bak

cat LinuxInstaller.bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_Kernel/" > LinuxInstaller.bin

- after that, run the installer as normal and it should work

---

### Post by Jeanpaul145 on 2008-03-02
> **mark_sfu said:**
> I ran into the same issue while installing maple 9.5 for linux on Feisty. However, searching on google, I found this fix for the same problem but for a different program

[http://www.zend.com/support/knowledgebase.php?kbid=184&view_only=1](http://www.zend.com/support/knowledgebase.php?kbid=184&view_only=1)

here are the adpated instructions to make this work for maple:

- copy the cd contents to the hard drive
- go to the directory /Linux/Disk1/InstData/VM or wherever the file LinuxInstaller.bin is located
- then do the following two commands

cp LinuxInstaller.bin LinuxInstaller.bin.bak

cat LinuxInstaller.bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_Kernel/" > LinuxInstaller.bin

- after that, run the installer as normal and it should work

Thanx man, helped me out a lot!

---

