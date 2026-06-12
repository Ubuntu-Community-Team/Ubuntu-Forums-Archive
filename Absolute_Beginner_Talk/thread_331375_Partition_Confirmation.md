---
title: "Partition Confirmation"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by utrob on 2007-01-04
This should be nice and simple to answer (I hope) but I just need straight confirmation whether I'm doing this right.

Basically i have two partitions currently. Each ~112GB. One has winxp on it (C:) and the other (K:) is unformatted.

When i go to install I am given the option of resizing one partition and another option of erasing. Is the first option correct (the drive name has no size figure associated with it therefore i assume it's the unformatted one) and can i be sure this won't alter my Win XP installation - which is vital by the way!

Ps this is for dual booting ubuntu and winxp pro

I hope this is enough information for an answer.

---

### Post by Bartender on 2007-01-04
It's a good idea to make absolutely sure how Linux is identifying your partitions.  With your LiveCD, go back to the desktop.  You know, where you have the little "Install" icon.  Go to System>Administration>Gnome Partitioning Tool.  Click on that and take a good hard look at the map it brings up.  If you have a thumb drive, plug it in, then go to Applications>Accessories>Screenshot and take a screenshot.  Save it to your thumbdrive.  It should show up in the list of places to Save.
If you don;t have a printer that's recognized by Ubuntu, get out entirely, boot to Windows, and print out that screenshot.  You want that right next to you when you're back in the installer.

OK, so you've already partitioned and the second one is blank.  Is the second partition labeled '/dev/hda2'  or '/dev/sda2'?  I'm guessing it will be.  

And is the first one hda or sda1?  And that one's formatted as NTFS?  We want to make sure which one is Windows and which one's blank! 

If you've already got your partition built, then you don't want to resize or erase.  You'll probly want to go into "manually partition" and mount / to hda2.  Also mount swap to hda2.  Take a look at aysiu's website for more info.
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by utrob on 2007-01-04
The first one (with winxp on) is formatted as NTFS and was partitioned when I installed windows. I'll just check regarding dev/hda2 etc now.

Thanks for the quick reply!!

---

### Post by utrob on 2007-01-04
From gnome this is how my partitions look.
sda1  fat16  70.57mb
sda2 ntfs 112.3Gb   Boot Flag
sda3 extended 117.35Gb   lba Flag
   sda5 unknown 117.35Gb  lba Flag
sda4 fat32  3.10Gb

sda2 must be Windows. So i'm either installing ubuntu on sda3 or sda5 - apparently the same space?

---

### Post by ajgreeny on 2007-01-04
I think sda1(uncertain whats in that) and sda2(windows) are primary partitions.
Sda3 is probably an extended partition containing sda5, a virtual partition (exactly the same size, as you noted).
I can't imagine what sda1 or sda4 are or why they're there, unless one is a boot partition and the other a restore partition put on the hard disk by the machine manufacturer when windows was installed.

---

### Post by utrob on 2007-01-04
I believe that is exactly what sda1 and 4 are (although not flagged). Would i be installing Ubuntu on the virtual partition sda5 or sda3?

Thanks for the reply!

---

### Post by Bartender on 2007-01-05
Hey, there, aj -
Seems like there's been a run of these partitioning threads lately.  Or maybe I'm just drawn to them like a magnet.  A lot of these "big-box" PC's from HP or Dell or whatever have these goofy little partitions plugging up the works.  The little vfat partition *in front of* the main OS partition appears to be some sort of Media Direct or utility partition that does proprietary stuff, then the larger partition on the other side is recovery.  
If the person has a recovery CD, or can go ahead and make one from the data in the recovery partition, I think the best thing to do is delete that partition, giving yourself a little more leeway for Linux partitions.
Just my opinion.

---

### Post by utrob on 2007-01-05
Thanks for the reply. I managed to do it last night. I left the small partitions and my winxp one alone. And split within the extended partition to leave me with a root partition of 105Gb and a swap of 2Gb and 9GB for something else i think. But yeah, took a lot of guts to go for it :P 

Thanks for the help! Just graphics and internet to sort now ;)

---

