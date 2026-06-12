---
title: "Ubuntu's ability to access other files/2 OS's sharing a partion with MP3's"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Aryding on 2007-08-23
So I currently am on the move to Ubuntu from Windows XP.  I am going to be keeping Windows XP while I play around with Ubuntu and make the decision to stick with it or not.

Here's my problem:

I have MP3 files (about 20GB) that I want XP and Ubuntu to have access to.  How can I make this work?  I was thinking of creating three partitions on my drive (One for XP, one for Ubuntu, and one for the music files).  I also heard Wubi will allow access to XP files... but I don't want any performance disadvantages from using Wubi.

What do you think?  Am I asking for a headache here?

My Specs:

ASUS W3J
2 Ghz Core Duo
ATI x1600
100GB HDD

---

### Post by ErusGuleilmus on 2007-08-23
I have a Vista partion and an ubuntu partion. i also have lots of MP3's. I can just go to the computer option under places, mount the volume, and access them. I was able to point Amarok to that particular destination in the windows volume, but I need to mount it first.

---

### Post by bodhi.zazen on 2007-08-23
> **Aryding said:**
> So I currently am on the move to Ubuntu from Windows XP.  I am going to be keeping Windows XP while I play around with Ubuntu and make the decision to stick with it or not.

Here's my problem:

I have MP3 files (about 20GB) that I want XP and Ubuntu to have access to.  How can I make this work?  I was thinking of creating three partitions on my drive (One for XP, one for Ubuntu, and one for the music files).  I also heard Wubi will allow access to XP files... but I don't want any performance disadvantages from using Wubi.

What do you think?  Am I asking for a headache here?

My Specs:

ASUS W3J
2 Ghz Core Duo
ATI x1600
100GB HDD

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Terl on 2007-08-23
I use ntfs3g and easily access my mp3's on the XP side from my Ubuntu side.  If you get the ntfs-config via synaptic when you get the ntfs3g it makes your setup a total breeze.

---

### Post by Aryding on 2007-08-23
So I'm guessing your telling me that I find the XP partition (with my MP3 files on it) through ubuntu, which will allow me access from there?

Errr... I went to reply and 2 more posts popped up... Thanks!

---

### Post by Aishiko on 2007-08-23
OR you could make a partition that was formated to FAT32 which both OSes can read and write to without problems.  Or downloading special drivers to read NTFS or EXT3 from windows.

---

