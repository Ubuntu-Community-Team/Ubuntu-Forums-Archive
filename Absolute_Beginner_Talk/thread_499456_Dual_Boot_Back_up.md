---
title: "Dual Boot Back up"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by dhopley on 2007-07-12
Dear Forum , 
Hi , Ubuntu newbie here with a dual booting Fiesty and Windows 98SE . I am still trying to set up an effective and reasonably co-ordinated backup method for my system . Windows 98SE does not have the CD drivers automatically loaded into MS DOS and so a boot up floppy with OakCDrom drivers was supplied together with the original 98SE set up CD in the last millenium when I bought the kit , and where the CDs can then be invoked from MS DOS with the drivers loaded . Without an equivalent Ubuntu set up floppy (or somehow utilising the alternate CDs boot loading technique) it is not possible for me to use the 'Live CDs' and in any case it's sounder practice to 'snapshot' a system's image in batch without the distraction of on line operations effecting changes to the system being backed up . After significant trial 'n error I have now each of the dual boot operating systems on 10g disks and backed up to my common 20g backup disk .
The method used the 98SE boot floppy to load the Norton Ghost 2003 CD and :
A>D:
D>CD GHOST/SUPPORT
D:\GHOST\SUPPORT ghost -clone,mode=copy,src=2,dst=3 -span -ial -szee 
This overwrote my back up disk previously formatted with FAT32 with the three Ubuntu partitions in a disk to disk copy with spanned files (overcoming the 2G native MS DOS limit) , ial gives a sector by sector copy of Linux files (EXT2 or EXT3 it claims) and szee to keep input and output partitions the same size .
Reboot back into MS DOS and use FDISK to use the second half of the backup disk as a DOS PRIMARY Partition and FORMAT it to FAT32 .
Reboot back into MS DOS and invoke Norton Ghost as before
D:\GHOST\SUPPORT ghost -clone,mode=create,src=1,dst=D:\D7710.gho -span z3  
This writes a C: drive image to the Windows file D:\D7710.gho and z3 with maximum compression  
I'm reasonably confident with the Windows backup as I have used such backups and recovered to my snapshot system image previously (@ 20 mins a shot back up/restore) , but the Ubuntu system I'm much less familiar with and wonder if there's an easy way to check the backup out with FSCK etc . The FAT32 back up partition (Hdc4) I've added to Ubuntu start up /etc/fstab and etc/mtab files and it's mounted fine at start up together with Hda1 the 98SE system disk , but I'm nervous about confusing Ubuntu/Grub too much by loading a disk copy of Hdb1,Hdb2 and Hdb3 as Hdc1,Hdc2 and Hdc3 as I'm already getting intermittent tty job control initramfs errors at start up , which after viewing other posts I'm attributing to confusion with UUIDs . Will Ubuntu flip if I include the full system copy Hdc partitions at start up and are there any straight forward ways to check the viability of the backup other than with a 'Russian roulette' restore ? Any comments on the above greatly welcomed ,        
Derek

---

### Post by phr0ze on 2007-07-13
If you can manage to get another drive you could remove the good drive, put in a spare and try to do your full restore on it. Not many of us here have struggled with all these dos boot limits in a while. Are you sure your BIOS doesn't support CD booting?

---

### Post by Hendrixski on 2007-07-13
> **dhopley said:**
> Dear Forum , 
Hi , Ubuntu newbie here with a dual booting Fiesty and Windows 98SE . I am still trying to set up an effective and reasonably co-ordinated backup method for my system . Windows 98SE does not have the CD drivers Derek



Hey Derek,

What it sounds like to me is that you just want to get rid of the windows 98... It's almost a decade old!  replace it with a brand new, modern operating system.  So just backup some data, and install Ubuntu.  
The live CD can do miracles... you can back up to an external driver, you can recover lost data (not easily, but it is do-able) you can move data between partitions... etc..

---

### Post by Hendrixski on 2007-07-13
And since you're new I thought I would give you a warm welcome that comes from the heart...


WELCOME TO THE COMMUNITY!
We're all here to help new Ubuntu users because we love ubuntu, and we want to share our joy with others.  Some of us here are even the same people who write the software you're using, or the documentation you're reading.  Why?  because we value freedom so we built a platform that is free.

If you prefer chatrooms then you should totally check out the channel #ubuntu on IRC. Installing IRC is easy and fun. Just go to applications-->Add/Remove and pick XChat from the list, click OK and you're done.

You can meet other Ubuntu users in your area too! Just check out the Ubuntu LoCo teams for your city or state.

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it. A lot of it is written by the same people who answer questions on these forums. If dry manuals aren't your thing then relax and watch some videos. [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc. Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

