---
title: "Ubuntu 12.04 Installation issues"
date: 2014-12-14
forum: Apple Hardware Users
---

### Post by crafterguy1701 on 2014-12-14
So i have been searching the internet a while and havent found anything on this.  I am trying to install Ubuntu 12.04 PPC Alternate 32 bit on a Power Macintosh 7500
Here are the system specs:

Mach Speed G3 @ 400 MHz

240 MB RAM

5 GB SCSI hard disk drive (plus a 16 GB external USB drive)


I use Bootx to boot off of the CD and it brings me to the normal alternate install dialogs.  I setup an Ext4 Journaling filesystem for root at about 4.6 GB.  Then i setup a swap partition at 250 MB
Then the home partition with an Ext4 Journaling filesystem at 15.8 GB.  When its installing the base system it fails to unpack certain packages (dont know what those packages are) and it says it will retry 5 times.  It retries about 2-3 times and then continues.  The next thing it complains about is failing to configure certain packages (again it doesnt specify what they are).  Then the last thing is it fails to install the kernel.  Though it did specify what kernel it was trying to install and it had the SMP bit at the end (i think thats for multi core/processor systems) and that might be the problem.  Otherwise im not sure.  Any help appreciated

EDIT:
I forgot to mention the "Mach Speed G3" thing is the name of the processor card i installed, it is in no way shape or form me hinting at it being "Mach Speed" by todays standards.
Also, i found that 12.04 no longer has the non-SMP kernel for 32 bit systems.  Will an SMP kernel work in a machine with a single core/single processor?  If not is it possible to install an older non-SMP 32 Bit kernel?

---

### Post by rsavage on 2014-12-14
You need something slimmer than Ubuntu, maybe Lubuntu?  It could be that you've just run out of space on the hard drive?  4.6GB is not a lot.  Try using the cli option to install a command line only install.

Have you seen this thread about Bootx [http://www.mintppc.org/forums/viewtopic.php?f=10&t=1237&p=8080](http://www.mintppc.org/forums/viewtopic.php?f=10&t=1237&p=8080) ?

SMP will work with single core, so that's not the problem.

---

### Post by crafterguy1701 on 2014-12-14
I am using the whole 4.6 GB hard drive for the root partition.  The external USB drive has home and swap.  I do not think space is an issue but im not sure.  I am only on the step for installing the base system so 4.6 gigs ought to be enough (i  would think)  I can try the old world bootable CD method but A. im not sure how to make a "fake" system folder and B. i dont have many CDs lying around.  Point me to a hard drive boot method?

The article i originaly found detailng what im doing is here: [https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

---

### Post by rsavage on 2014-12-15
Sorry, I gave you the wrong link, it should of been [http://www.mintppc.org/forums/viewtopic.php?p=5594#p5594](http://www.mintppc.org/forums/viewtopic.php?p=5594#p5594) .  Maybe worth a read?  I know nothing about oldworld macs.Hard drive boot method for new world macs is in the FAQ.

---

