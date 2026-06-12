---
title: "Mount Point?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by gyzer on 2008-04-12
I'm installing Ubuntu 8.04 for the first time on my computer. I just selected it to format the drive where I want Ubuntu 8.04 to install, and now its asking me to define a Mount Point. What is a Mount Point? 

The mount point that it will do is "/media/sda1" or it will allow me to do one that is "/dos" or "/windows".

Any clarification on this would be really appreciated.

---

### Post by drdrewdown on 2008-04-12
its asking for a mount point of the filesystem

where ever you want to install linux to should be a /

simply a / defines a root directory for the filesystem to be installed.

good luck

---

### Post by gyzer on 2008-04-12
So then can the mount point just be "/"? Or should I do something like "/root"?

What does "sda1" stand for?

---

### Post by Tyke91 on 2008-04-12
just put /  for the filesystem where the operating system will be installed. other popular mount points for systems are /home and /boot, but just having / will mount all the appropriate files where they need to be. mount point names are not really customizable at this level. they are useful if you want to devote an entire hard drive to your personal data (/home) or your boot sector (/boot)... you can even add a hard drive later that is specifically for your music (/home/Music)... but a /windows mount point would kind of break the system. here's a page that explains it. scroll down for a diagram

[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

[http://tldp.org/LDP/intro-linux/html/images/FS-layout.png](http://tldp.org/LDP/intro-linux/html/images/FS-layout.png)

sda1 means the first SATA hard drive

---

### Post by drdrewdown on 2008-04-12
the / is what you are looking for

/ is the root directory :)

the sda1 is the label applied to your first sata disk usually.

---

### Post by joshrobinson on 2008-04-12
> **gyzer said:**
> So then can the mount point just be "/"? Or should I do something like "/root"?

What does "sda1" stand for?

you have to use /

sda is a hard-drive thats probably sata, this identifies the disk
sda1 is partition #1 on drive sda

if you have 2 sata drives, you will see an sda and an sdb, and so on
it helps identify what disc is what

normal ide drives show up as hda, hdb etc

---

### Post by gyzer on 2008-04-12
thanks for the quick responses

---

### Post by gyzer on 2008-04-12
Ok now, I wanted to format this drive in FAT32, and now its saying that its an invalid file system for this mount point, and that I should choose a differnt file system such as ext2. I thought that Linux operating systems can run on FAT32?

---

### Post by Tyke91 on 2008-04-13
out of curiosity, why do you want to use FAT32? if you use ext2 or (recommended) ext3, you won't have to defragment. also, I believe there is a file size limit on fat32

if you want your windows install to see ubuntu, install this [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

