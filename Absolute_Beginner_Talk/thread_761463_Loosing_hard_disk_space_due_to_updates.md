---
title: "Loosing hard disk space due to updates"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by rajaram_s on 2008-04-21
I have about 20 GB for my linux partition. It once had 19 GB free space, when I installed a few repos and some other desktop environments to get it to around 16 GB. I only keep installing updates since then, and dint download much of repositories either. After few months, I find my drive now hardly has 5 GB of space remaining. Do updates really take space? Is there anyway to avoid them using up my disk space? Dont the updates go and erase the previous versions?

---

### Post by SnakeHips on 2008-04-21
scroll down to post 4

[http://ubuntuforums.org/showthread.php?t=664742&highlight=disk+cleanup](http://ubuntuforums.org/showthread.php?t=664742&highlight=disk+cleanup)

---

### Post by tzulberti on 2008-04-21
The previous versions of the programs are deleted when you update a program. To delete things you don´t use you could use:
-> sudo apt-get clean: It deletes all the download deb packages.
-> sudo apt-get autoclean: It deletes all the donwload deb packages that aren't the ones that corresponds to the new version (ie the deb packages of old versions).
-> Install deborphan: this program list you the packages that were once installed, but that are no longer necesary.

Nevertheless, the update don't take much disc space...

---

### Post by zvacet on 2008-04-21
@ **rajaram_s**

If you don´ have separate home partition then all your files(text files,music,movies...)take some space and that can be reason why you have so little of free space.Updates can not take so much space.

---

### Post by philinux on 2008-04-21
System>admin>system Monitor.

Click the file system tab. In Edit Preferences file systems tab check show all file systems.

This will show you where your disk usage is.

---

### Post by rajaram_s on 2008-04-23
ya... thanks, using autoclean cleaned up around 300MB of my disk space... reast, I still dont know how............

---

