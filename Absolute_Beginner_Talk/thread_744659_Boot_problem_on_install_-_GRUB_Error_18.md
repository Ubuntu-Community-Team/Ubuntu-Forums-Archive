---
title: "Boot problem on install - GRUB Error 18"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by sabedor on 2008-04-03
I have a PC and a used harddrive.  I tried to install Ubuntu on that drive using LiveCD and it went OK even though I was not sure what I was doing.  The confusing part is how to handle the partition.  It is a 160 GB drive and had 90 GB of data on it in FAT32 format.  I created a partition in the unused area and that worked, but when I boot, I get a GRUB Error 18 during State 1.5.  From what I have found, it is probably a problem with the bios trying to run from a sector that is not withing the first 512 MB.  The suggestions keep saying to just add a boot partition in the first part of the disk but they never say how to do that.  So can I add a boot partition where the bios will like it, but not ruin the data that exists on the drive?

Here is FDISK:

root@ubuntu:~# fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0df0954a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15713   126214641    c  W95 FAT32 (LBA)
/dev/sda2   *       15714       19788    32732437+  83  Linux
/dev/sda3           19789       19929     1132582+   5  Extended
/dev/sda5           19789       19929     1132551   82  Linux swap / Solaris

Thank you in advance.

---

### Post by drcdebaca on 2008-04-03
I had the exact same problem yesterday.  You need to manually configure your hard drive with at least a 32 MB partition that is ext2 and the rest of the drive ext3.  Hope this works for you.  Best of luck.

---

### Post by sabedor on 2008-04-03
Thank you for the suggestion.  How do I do that?  Then, when it is made, do I have to re-install ubuntu or something?

---

### Post by ryan22158 on 2008-04-03
> **sabedor said:**
> Thank you for the suggestion.  How do I do that?  Then, when it is made, do I have to re-install ubuntu or something?

Use Gparted live CD, google it.

It worked for my swap file problem. Brilliant me decided to not make my swap big enough to hibernate is I had to repartion my drive with it. It is a very simple straight foward kinda thing.

---

