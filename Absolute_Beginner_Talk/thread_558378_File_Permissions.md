---
title: "File Permissions"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by larrylwill on 2007-09-23
I am trying to learn Ubuntu I have it in a duel boot laptop with XP. Recently I downloaded a program that only works in Xp I tried to copy it to the XP partition but it wont let me. I opened permissions but it says " You are not the owner so you can't change permissions" 
Question: How can I copy a file from Ubuntu to the XP partition?
Thank you

---

### Post by Maestro23 on 2007-09-23
Install ntfs-3g and ntfs-config

> sudo apt-get install ntfs-3g

sudo apt-get install ntfs-config



Provides read/write access to a NTFS partition from Ubuntu.  Link to the website for info: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by Hospadar on 2007-09-23
> **Maestro23 said:**
> Install ntfs-3g and ntfs-config



Provides read/write access to a NTFS partition from Ubuntu.  Link to the website for info: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

Yah, it's not really that you don't have access, but unless you have write-capable drivers installed, ubuntu will automatically set the permissions to be read-only so you don't mess up the drive. ntfs-3g and ntfs-config work great.  once you install them run "ntfs-config" from the command line.

---

### Post by larrylwill on 2007-09-24
I did as you said but I still cant copy a file to my other partition. I have the same problem.
 It added an NTFS configuration tool to my system tools menu .
I ran it and named a disk but still can't copy a file from Ubuntu to the xp partition, although I can see the files and copy them from xp to ubuntu.



larry@ubuntu:~$ sudo apt-get install ntfs-3g
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
larry@ubuntu:~$ 
larry@ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ntfs-config
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 42.5kB of archives.
After unpacking 442kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe ntfs-config 0.5.5-0ubuntu1 [42.5kB]
Fetched 42.5kB in 21s (1982B/s)                                                
Selecting previously deselected package ntfs-config.
(Reading database ... 110065 files and directories currently installed.)
Unpacking ntfs-config (from .../ntfs-config_0.5.5-0ubuntu1_i386.deb) ...
Setting up ntfs-config (0.5.5-0ubuntu1) ...
larry@ubuntu:~$

---

### Post by larrylwill on 2007-09-24
larry@ubuntu:~$ ntfs-config

** (ntfs-config:11488): WARNING **: Error : This programm need to be run as root.

---

### Post by moffa on 2007-09-24
Applications > System Tools > NTFS Configuration Tool

If that doesn't work in a terminal ```
 gksu ntfs-config 
```

---

### Post by larrylwill on 2007-09-24
Yes I have tried both, I get enable write support for internal and external devices and both are checked but Im still locked out. I used Wubi to load Unbunto if that means anything. Im about ready to go back to XP. Such a simple thing to gain access to another drive shouldnt be such a large problem.

thanks

Here is what happened when I unchecked enable write support.

larry@ubuntu:~$ gksu ntfs-config

** (ntfs-config:12725): WARNING **: Mounting /media/xp drive failed.

mount: /dev/sda5 already mounted or /media/xp drive busy

---

### Post by larrylwill on 2007-09-25
Well allrighty then, I guess there is no soulition to this problem.

---

