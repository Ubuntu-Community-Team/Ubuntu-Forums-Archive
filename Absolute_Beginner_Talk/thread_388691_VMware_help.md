---
title: "VMware help"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-19
I am using this guide.
[http://www.ubuntuforums.org/showthread.php?t=183209]("http://www.ubuntuforums.org/showthread.php?t=183209")
I dont think it is installing right.
Here is what happens:
```
ben@ben-ubuntu:~$ cd /tmp
ben@ben-ubuntu:/tmp$ cd vmware-server-distrib
ben@ben-ubuntu:/tmp/vmware-server-distrib$ export CC=/usr/bin/gcc-3.4
ben@ben-ubuntu:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Server 1.0.2 build-39867 for Linux completed 
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/home/ben/vmware] /home/ben/vmware

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/tmp/vmware-server-distrib/lib/serverd] 

In which directory do you want to install the daemon files? 
[/home/ben/sbin] 

The path "/home/ben/sbin" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] 

In which directory do you want to install the library files? 
[/home/ben/lib/vmware] 

The path "/home/ben/lib/vmware" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want? 
[yes] 

In which directory do you want to install the manual files? 
[/home/ben/man] 

The path "/home/ben/man" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] 

In which directory do you want to install the documentation files? 
[/home/ben/doc/vmware] 

The path "/home/ben/doc/vmware" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want? 
[yes] 

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

```

Any help?

---

### Post by zvacet on 2007-03-20
Is this your first install?I ask you that because it´s seams that you have another installation of vmware server.If that is the case you have to uninstall all vmware server files and start fresh.

---

