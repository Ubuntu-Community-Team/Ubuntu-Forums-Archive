---
title: "C:\Program Files"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by WarMonkey on 2008-04-02
What is the Ubuntu version of program files called?

---

### Post by Tatty on 2008-04-02
There is no equivalent of that in Ubuntu.

linux software doesnt get grouped together in its own folder like it does in windows... It gets split between different parts of the system.  For example /bin are all the binary files /etc are all the user configurable files, etc...

I read an interesting article once on how linux filesystems are organised... ill post it if i can find it

---

### Post by bren on 2008-04-02
Table 3-2. Subdirectories of the root directory
Directory	Content
/bin	Common programs, shared by the system, the system administrator and the users.
/boot	The startup files and the kernel, vmlinuz. In some recent distributions also grub data. Grub is the GRand Unified Boot loader and is an attempt to get rid of the many different boot-loaders we know today.
/dev	Contains references to all the CPU peripheral hardware, which are represented as files with special properties.
/etc	Most important system configuration files are in /etc, this directory contains data similar to those in the Control Panel in Windows
/home	Home directories of the common users.
/initrd	(on some distributions) Information for booting. Do not remove!
/lib	Library files, includes files for all kinds of programs needed by the system and the users.
/lost+found	Every partition has a lost+found in its upper directory. Files that were saved during failures are here.
/misc	For miscellaneous purposes.
/mnt	Standard mount point for external file systems, e.g. a CD-ROM or a digital camera.
/net	Standard mount point for entire remote file systems
/opt	Typically contains extra and third party software.
/proc	A virtual file system containing information about system resources. More information about the meaning of the files in proc is obtained by entering the command man proc in a terminal window. The file proc.txt discusses the virtual file system in detail.
/root	The administrative user's home directory. Mind the difference between /, the root directory and /root, the home directory of the root user.
/sbin	Programs for use by the system and the system administrator.
/tmp	Temporary space for use by the system, cleaned upon reboot, so don't use this for saving any work!
/usr	Programs, libraries, documentation etc. for all user-related programs.
/var	Storage for all variable files and temporary files created by users, such as log files, the mail queue, the print spooler area, space for temporary storage of files downloaded from the Internet, or to keep an image of a CD before burning it.

more here [http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

---

### Post by Oldsoldier2003 on 2008-04-02
> **WarMonkey said:**
> What is the Ubuntu version of program files called?

there really isnt a "program files" directory in Linux. There are some accepted standards as to where executables should be placed.[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) is a good place to read up on the subject. If you need to find the path of a program you can type this in a terminal:
```

which <program_name>
```

---

### Post by SunnyRabbiera on 2008-04-02
The closest is usr/bin or usr/lib, those are where your applications are mostly put at depending on the app.

---

### Post by jflaker on 2008-04-02
This?
[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

---

### Post by SunnyRabbiera on 2008-04-02
actually I find this useful to cover the basics:
[here]("http://www.freeos.com/articles/3102/")

---

### Post by kool_kat_os on 2008-04-02
Ubuntu doesn't really have a root like that.

---

