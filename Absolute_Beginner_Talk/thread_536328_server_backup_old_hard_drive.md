---
title: "server backup old hard drive"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-08-27
I now have a apache2 and postmail server running thanks to this list.
What I would now like to do, is use one of my smaller old hard drives to 
back up the complete setup all files everything. Then remove it from the 
system. What would be the easy way of doing this and do I have to have 
the same size partitions.

Second question is there a defrag utility for ubuntu or does it not need this

Larry

---

### Post by ddrichardson on 2007-08-27
Fragmentation isn't really an issue and is dealt with by fdisk. As for backing up to an old drive, try cloning the disk - [system rescue cd]("http://www.sysresccd.org/Main_Page") can do it easily by fitting the drive, running the livecd, backing up, uninstalling the drive then going back into the installed OS.

---

