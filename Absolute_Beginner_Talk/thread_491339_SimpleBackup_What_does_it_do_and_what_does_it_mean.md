---
title: "SimpleBackup: What does it do and what does it mean"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-07-03
Hi I'm trying to figure out the best way of doing my backups in ubuntu. I'm using SimpleBackup from the repositories, but I'm not really sure what Im doing with it. I have configured it to backup my home directory, my etc, var, and usr directory. What is all that? if my system goes down can I then get it all back from baccking up those directories?
I want to be able to get everything back if my harddisk crashes, programs settings drivers, everything. I have spent weeks on getting my video card drivers working and I'm not going through that process again. Which folders do I need to include in my simple backup configuration so that I can get everything back when Im unlucky.

And one last question: In windows I used a backup program from symantec called ghost backup, that could make and image file from my harddisk and recover it again from a boot disk. Is there a program for linux that can make an image file from my entire harddisk that I would be able to use as recovery to get the whole os back again?

---

### Post by the.phantom on 2007-07-03
well i use partimage on a self booting disk and it is like ghost

or you could try g4l   ( ghost for linux)

they are both total backup programs

---

### Post by Rocket2DMn on 2007-07-03
I use SimpleBackup but have never had to restore (it's only been a few weeks), but the program has a Restore.  I think it's under System->Admininstration->Simple Backup Restore, but I'm not in front of my Ubuntu computer to check.
The program will make a full backup of the directories you select and store them in a tar.gz (or .tgz file, I don't recall) on your external drive.  Afterwards it makes incremental backups based on files that are new or have changed.
Should you suffer a complete system failure and have to start fresh, you should be able to reinstall Simple Backup and run the restore based on the backups you have on your external drive.

I'm not sure about imaging the disk - there must be a way, and I'd be glad to hear how from anybody else.

---

