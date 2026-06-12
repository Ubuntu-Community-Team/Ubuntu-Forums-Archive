---
title: "[SOLVED] Linux Directory Hierarchy"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by jeremy.oakes on 2008-02-20
Okay... I've searched, and searched, and searched and even a little bit of scouring. I still cant seem to find a good explanation of the entire Linux Directory hierarchy.

I'm still somewhat new to Linux, and I've come to understand what some of the directories are used 
such as /home and /bin. 

It seems the /etc folder contains the system configuration files.. is that right?
This might even become a good basis for a FAQ for other new folks like myself.


Can someone provide a clear explanation of what the following directories are used for?
/bin
/boot
/dev
/etc
/home
/initrd
/lib
/lost+found
/media
/mnt
/opt
/proc
/root
/sbin
/srv
/sys
/tmp
/usr
/var

Also, would like some help explaining the following:
  1. What is the difference between /bin and /sbin?
  2. What is the difference between the /usr/* folder and the /* equivalents (i.e. /usr/bin vs /bin)

---

### Post by kellemes on 2008-02-20
Couple of links..
[http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/](http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/)
[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

---

### Post by jan quark on 2008-02-20
the classic answer

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by ahsile on 2008-02-20
I'm by no means an expert... and this is just what I've picked up along the way.

> **jeremy.oakes said:**
> 
/bin - Binaries (programs)
/boot - This is where grub/lilo load your kernel from
/dev - devices (this is a virtual file system )
/etc - configuration files
/home - user directories
/initrd - this is where you initialization scripts for server programs (daemons) exist
/lib - shared libraries (sort of like your system32 folder for dlls in windows)
/lost+found
/media - this is where removable media is mounted (CDs/Flash drives/etc)
/mnt
/opt
/proc
/root - this is the root user's home folder
/sbin - server programs
/srv
/sys
/tmp - temporary files
/usr
/var



It may not be entirely correct, and I'm sure someone else can fill you in where I've missed out....

---

### Post by philinux on 2008-02-20
This is a nice image that explains it.

---

### Post by jeremy.oakes on 2008-02-20
Fantastic!

Thanks All!!!!

---

