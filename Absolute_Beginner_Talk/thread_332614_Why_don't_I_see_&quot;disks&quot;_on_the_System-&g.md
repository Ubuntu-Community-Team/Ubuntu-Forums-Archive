---
title: "Why don't I see &quot;disks&quot; on the System-&gt;Administration menu?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by tc101 on 2007-01-06
I am running 6.10 from the DVD.  I want to look at some files on my hard drive from linux.  The first step in the online help says:

Open System->Administration->Disks 

However, when I open System->Administration I do not see any "Disks"
item on the menu.  

Any idea why I don't see "disks" on the System->Administration menu?

---

### Post by meng on 2007-01-06
That's because it's not there in Edgy. There is a Disk Usage Analyzer, which you can access from alt-f2, list known applications.

---

### Post by bapoumba on 2007-01-06
Hi,
Disk Usage Analyser is [baobab]("http://www.marzocca.net/linux/baobab.html") which made it to gnome-utils. You may have to use > System > Prefs > Menu layout to have it in accessories menu.

---

### Post by tc101 on 2007-01-06
I hit alt-F2 and ran the disk usage analyzer.  It is just showing me the DVD I have booted ubuntu from, and not the hard drive on my computer.

I am trying to read some files from the hard drive using unbutu because it has a pirated version of win XP which MS has somehow detected and will not let me run until I call them.  I backed up almost all of the important stuff but there a few things I want to get off the disk before I wipe it clean and install unbutu.  

Booting from the 6.10 DVD, how do I see the files on my hard drive, and copy them to a CD or floppy?  In this computer I have the DVD that I am running from, a RW-CD, and an old floppy drive.

---

### Post by meng on 2007-01-06
Okay, drop down to terminal and run
sudo fdisk -l
(l as in larry)

---

### Post by tc101 on 2007-01-06
I went to terminal and did what you said and got what I have pasted below.  It is showing my HD which is 80 GB.  However, when I do alt-F2 and run Disk Usage Analyzer what I am seeing is the DVD I have booted from.

Here is what I did in terminal:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by meng on 2007-01-06
My suggestion:
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1 -t ntfs -o nls=utf8,fmask=0333,dmask=0222
cd /media/hda1

You should be able to browse the files.

---

### Post by tc101 on 2007-01-06
After doing

sudo mount /dev/hda1 /media/hda1 -t ntfs -o nls=utf8,fmask=0333,dmask=0222

I get this message:

mount: special device /dev/hda1 does not exist

---

### Post by meng on 2007-01-06
?? fdisk showed it was there! I'm stumped.

---

### Post by Bartender on 2007-01-06
We were talking about "Disks" a few days ago.
[http://ubuntuforums.org/showthread.php?t=328951](http://ubuntuforums.org/showthread.php?t=328951)

---

### Post by Frank Golden on 2007-01-06
> **tc101 said:**
> After doing

sudo mount /dev/hda1 /media/hda1 -t ntfs -o nls=utf8,fmask=0333,dmask=0222

I get this message:

mount: special device /dev/hda1 does not exist
I think the command should be [COLOR="Red"]sudo mount -t ntfs /dev/hda1 -o nls=utf8,fmask=0333,dmask=0222  /media/hda1[/COLOR]
or just [COLOR="red"]sudo mount -t ntfs /dev/hda1 /media/hda1[/COLOR]
then [COLOR="red"]cd to /media/hda1[/COLOR] or [COLOR="red"]gksudo nautilus /media/hda1[/COLOR]

---

### Post by Duck2006 on 2007-01-06
Can you try a KNOPPIX live cd

---

