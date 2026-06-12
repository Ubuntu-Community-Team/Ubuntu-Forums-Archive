---
title: "problem with gparted"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by japc126 on 2006-11-18
When I try to resize a ntfs partition with gparted, it returns an error message. What do I do? please help, I'm desperate.

Also, when I insert my xp install disk, it sais it doesn't detect any hard disks. What do I do?

---

### Post by aidanr on 2006-11-18
whats the error message, is the disk sata or ide?

---

### Post by japc126 on 2006-11-18
i think its sata, but how can i make sure? The pc is from dell, maybe that helps

---

### Post by japc126 on 2006-11-18
by the way, I can't install ubuntu without wiping out the hard disk. Im connected through the live cd of ubuntu

---

### Post by japc126 on 2006-11-18
the error message:

An error occurred while applying the operations
The following operation could not be applied to disk:

Resize /dev/sda2 from 70.95 GiB to 65.56 GiB

See the details for more information

---

### Post by aidanr on 2006-11-18
[http://i2.photobucket.com/albums/y38/muaz/sata-ide_lg.jpg](http://i2.photobucket.com/albums/y38/muaz/sata-ide_lg.jpg)
top one is ide, bottom is sata, i was going to say that if it was sata you may need to set the disk up properly in the bios first, but seeing as it is a dell that should already be done

what are the details of the error message that you get, also try resizing it from the [gparted live cd]("http://gparted.sourceforge.net/livecd.php") instead of the ubuntu live cd

---

### Post by japc126 on 2006-11-18
i tried to do it from the gparted live cd but it didn't work. I have been resizing for a while now, even had Ubuntu installed but had to remove it, and now windows won't start, the setup cd doesn't recognize my harddisk and... and... i don't know what to do.:( :( :( :( :(

---

### Post by aidanr on 2006-11-18
are you using the latest gparted, 0.3.1?
[http://gparted.sourceforge.net/larry/livecd/main/livecd.htm](http://gparted.sourceforge.net/larry/livecd/main/livecd.htm)
see the third screenshot there "load extra SCSI or SATA modules", may be worth a shot

---

### Post by moshuptrail on 2006-11-18
gparted will not resize an NTFS partition that has bad blocks.  That sounds like the error you are getting - not very descriptive, is it.  If you check things out and decide that's the case, you will need to use ntfsresize from the command line.  It's on the gparted live CD.  It's not a process for the feint of heart.

---

### Post by japc126 on 2006-11-18
continue helping me here [http://www.ubuntuforums.org/showthread.php?p=1776832#post1776832](http://www.ubuntuforums.org/showthread.php?p=1776832#post1776832)

---

### Post by mo79 on 2006-11-18
Have you checked the disk for errors? I bought a brand new drive for Ubuntu, but turns out it was a dud as Ubuntu installer/Gparted refused to do anything with it. Fine when I got a new one. Maybe you just have some simple probs that need clearing up first? Just my 2p.

---

