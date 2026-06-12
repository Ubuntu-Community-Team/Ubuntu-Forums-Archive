---
title: "Ubuntu/Linux directory structure/hierarchy"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by hendysg on 2007-04-26
I am new to ubuntu and linux in general. I've used it here and there while in college and now at work.

Ubuntu is making to move from windows to linux super easy. But I am still lost when it comes to its directory structure/hierarchy. Can somebody help explain what each following directory (and maybe others) is used for?

/bin
/dev
/etc
/mnt
/sbin
/tmp
/usr
/var

Thanks a bunch

---

### Post by mrpaco on 2007-04-26
I think [this]("http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/") will answer your questions and then some.

---

### Post by guardsman85 on 2007-04-26
Check out [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) for all the official info on the File Hierarchy Standards.  You'll probably want to download one of the PDF's.

Basically though here is how the directories are used:
/bin     Binary (executable) commands used by all users
/dev    Devices
/etc     System-specific configuration files
/mnt    Empty directory used for accessing (mounting) discs (e.g. CD-ROM or floppy)
/sbin   System binaries (i.e. administrative commands)
/tmp    Temporary files
/usr     Contains subdirectories which contain most system commands and utilities
/var     Variable-length files (e.g. log files)

Source:  *Linux+ 2005 - *Eckert, Jason W and M. John Schitka - Thompson Course Technology

---

### Post by hendysg on 2007-04-26
Thanks guys. Ubuntu Rocks!

---

