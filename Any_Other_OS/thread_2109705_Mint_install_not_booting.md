---
title: "Mint install not booting"
date: 2013-01-27
forum: Any Other OS
---

### Post by Dracodraconis on 2013-01-27
Hiya,

I was wondering if you guys could help me with my boot problem.

I refurbished my old laptop (HP HDX 18t) by buying a brand new hard drive.
Popped it into the computer.

Loaded mint14 onto a USB thumb drive and installed it onto the hard drive. I let it auto install and followed the guided menu during the installation (i.e. I didn't make any changes to partitions etc).

My issue is when I reboot, it keeps saying that the hard drive is not found. I am obviously able to fully boot into the USB live cd.

I used boot repair to see if it was an issue with MBR etc.

I took a snapshot prior to making any changes. Here it is : [http://paste2.org/p/2801599](http://paste2.org/p/2801599)

After this I used the "recommended repair" option. The snapshot taken after this is here: [http://paste2.org/p/2801602](http://paste2.org/p/2801602)

I have to admit that I am pretty much a complete linux newbie although I am a decent/power user on windows/mac and so would appreciate if you could help me make head or tail of why the hard disk can't be found during boot. 

Thanks!

---

### Post by oldfred on 2013-01-28
Moved to your own thread.

You may have the issue we sometime see where either BIOS settings or grub have issues with very large / (root) partitions.

Boot-Repair usually suggests a separate /boot at the beginning of the drive. I normally suggest a smaller 25GB / partition and use rest of drive as data partition or /home. 
Either way probably easier to reinstall.

But you can run a quick test and use gparted to shrink your current very large / to 50 or 75GB. You do not have a lot of data in it yet so it should not take long and about half the time that has worked when I have suggested it.

---

