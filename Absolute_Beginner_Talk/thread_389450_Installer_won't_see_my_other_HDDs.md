---
title: "Installer won't see my other HDDs"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by AMindForeverVoyaging on 2007-03-20
I'm a complete newbie to Linux - I tried installing Debian about a year ago, but was completely overwhelmed during the process, and never got the thing going. I heard Ubuntu was a lot more straightforward, so I thought I'd give it a shot.

The first hurdle I encountered was getting Ubuntu to load/install at all. After selecting  Load/Install (the first option) from the boot menu on the CD, I'd get an error message along the lines "Drive confused" and "no one cared". I did a search, and found a similar problem described here [http://ubuntuforums.org/showthread.php?p=1943381](http://ubuntuforums.org/showthread.php?p=1943381) and followed the suggestions (I even updated my motherboard BIOS). That sorta worked.

I've now loaded Ubuntu off the CD, and would like to install it to one of my hard drives, but I have a new problem. Step 5 of the installer - which asks me how/what to partition - only shows the 320gb hard drive that Vista is installed to. I have two other hard drives in my PC, one of which is an unpartitioned 180gb drive that I was hoping to install Ubuntu on.

Looking in the Device Manager, I can see that the 320gb HDD is the only one that Ubuntu sees. So, what do I have to do to get Ubuntu to see my other hard drives?

---

### Post by wpshooter on 2007-03-20
Are they partitioned and formatted ?

If not, have you tried running FDISK and FORMAT on them from a WIN98 boot diskette ?

---

### Post by AMindForeverVoyaging on 2007-03-20
I don't have a Win98 boot disk lying around. I suppose I could try and find one, but in the mean time...

Vista can see all three hard drives just fine. Two of them are partitioned and formatted NTFS. The third was the same, until yesterday when I deleted the partition in preparation for installing Ubuntu.

---

### Post by AMindForeverVoyaging on 2007-03-20
I've now tried using a Win98 boot disk. Using fdisk, I can see all three hard drives, and  I am able to partition them.

Ubuntu's device manager still only shows the one hard drive with Windows Vista on it. If the BIOS can see them, and a Win98 Boot disk can see them, why can't the Ubuntu Live CD see my other two hard drives?

---

