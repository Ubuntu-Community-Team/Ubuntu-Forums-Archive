---
title: "Ubuntu won't partition!"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by mudenza on 2007-05-26
Hello, I'm currently using XP pro on a IBM T42 lappie. Im using the Ubuntu alternate cd for installation and having problems installing Ubuntu on the right partition.

I want to have two operating systems on my hard disk, however, when I try to click on 'Guided Install' which would prompt me to resize my Windows partition, it says that there is an error (now I cant remember the exact error, but it just wouldnt allow me to resize). The same thing applies when I try to manual resize, it just won't budge.

I tried resizing my partition with PartitionMagic 8.0 with no success. Whenever I try to even open the program itself, it says that there is a problem identifying the disk letter (?), and then closes. My hard drive has no errors as I have already checked it for any bad sectors, and it is already formated in NTFS. 

Help!:(

---

### Post by smoker on 2007-05-26
hi, do you have plenty of empty space on your harddrive? also, it is advisable to get rid of any apps you don't use and junk files, etc, from you windows and defrag the drive a few times. scattered remnants of files all over the drive can give the resizer more work than it can handle, and maybe this is why you have an error.

best of luck

---

### Post by bigken on 2007-05-26
yep defrag windows and also clean up the system like smoker says I would also backup any imporant data 

Have you tried gparted liveCD the create your partitions ?

---

### Post by mudenza on 2007-05-26
Yeah I tried deleting most of my junk from my hard disk, defragged it to death until the blue bits became one big lump, but no luck. I have a total of 74 gigs, 4 of which are allocated to IBM_Service (Fat32), the rest to windows. I cannot use the liveCD as my ram is 256mb and it lags like it got hit by the plague...

---

### Post by smoker on 2007-05-26
hi, maybe try as bigken suggested the gparted live-cd and make your partitions before doing the install:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

best of luck

---

### Post by ugm6hr on 2007-05-26
> **mudenza said:**
> I cannot use the liveCD as my ram is 256mb and it lags like it got hit by the plague...

I think bigken was not talking about the Ubuntu LiveCD but the specific standalone GParted LiveCD.  I suspect your problem is that your current partition is NTFS, and partitioning that is not that easy.  The GParted LiveCD makes a good job of it, mainly because it has a newer version of GParted with better NTFS support.

Get it here if you want to try (backup first though):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I would suggest you try it out - burn the .iso and boot from the CD with the second boot option.  Then try to create your linux ext3 and swap partition there, before rebooting and trying to install Ubuntu in your new partition.

Very bizarre that PartitionMagic8 can't do the trick... not sure what to make of that

As for the issue with 256MB and speed - I can recommend Xubuntu7.04 (which I use and like).  The Xubuntu LiveCD will work just fine on your system, and will allow full easy installation.  If you want to go down that route - use GParted to just shrink the NTFS partition (leaving the rest empty, or with just an "extended partition" marker, and allow Xubuntu LiveCD just automatically install "using the largest unsused free HD space".  It will even take care of the swap partition for you.  

Downside of Xubuntu - no flashy graphics (but they would be unusable on your system anyway), and wireless networking requires marginally more work (essentially because Metwork Manager is not pre-installed).

---

