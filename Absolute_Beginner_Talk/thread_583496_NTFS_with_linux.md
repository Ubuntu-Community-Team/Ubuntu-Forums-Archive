---
title: "NTFS with linux"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by linux-loser on 2007-10-20
ok im running fiesty x64.  
i have a 80 gb sata drive thats not plugged in, taht drive is ntfs formatted but it has all my pictures, movies and music on it from when i used windows. can i just plug it in and access my stuff on taht drive or will i have to install something to allow me to access NTFS?  

any help would be awsome.

thank you for your time.

---

### Post by WinterWeaver on 2007-10-20
short answer... yes...

You can read all the files and copy from the drive. But, with Feisty you wont be able to Write or Copy TO the NTFS drive, without installing extra stuff.

With Gutsy you can Read/Write

WW

---

### Post by Paqman on 2007-10-20
Feisty can read NTFS, but needs a package called [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) to write to it. If you want to permanently mount the drive with write permissions you'll need to modify your fstab.

Gutsy has NTFS write built-in.

---

### Post by Maestro23 on 2007-10-20
> **Paqman said:**
> Feisty can read NTFS, but needs a package called [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) to write to it. If you want to permanently mount the drive with write permissions you'll need to modify your fstab.

Gutsy has NTFS write built-in.

Don't forget ntfs-config as well.

> sudo apt-get install ntfs-config

---

### Post by linux-loser on 2007-10-20
cool thanks all.  yay i can watch my movies again!

---

