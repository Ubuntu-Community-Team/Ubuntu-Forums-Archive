---
title: "Repartitioning confused grub (error 13 or 17)"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by gshyland on 2007-09-01
Hi, Linux / Ubuntu newb here. Thanks for help on the last issue...I'm back with more! :)

I had everything working fine in a 2 hard drive, dual boot system set up this way:

hd0: winXP, ntfs
hd1 partitions:  0- winXP, ntfs;  1- swap;  2- Ubuntu, ext3
grub in MBR of hd0 (I presume.)

...and then I decided I needed to add a FAT32 partition so I could share files between the two OS's.

Since WinXP had most of the space on hd1 I decided to shrink the NTFS partition by a few gigs and insert a partition there. The resulting partitions:
 0- winXP ntfs; 1- shared FAT32; 2- swap; 3- Ubuntu

In hindsight I should've known grub would not like the renumbered partitions.

After I did this my system wouldn't boot, not even XP! Thankfully I had made a grub CD which I used to reinstall the WinXP bootloader on hd0. So now, the system boots XP fine, but I must run grub from CD to boot Ubuntu.

I reverted the partition changes, getting rid of the added FAT32 partition. But, I can't get back to dual boot. 

Please bear with me, my info is not very good because I'm on that same PC. I'm sketchy about what happens while trying to boot. It might be time to get out the ol' pencil and paper and take some notes. :)

I could always start over from scratch: set up 4 partitions on hd1 the way I want, and install Ubuntu again. I know that works. But is there some easier way to get grub configured correctly and reinstalled in the MBR on hd0? Grub is puzzling me a bit, I'm not having much luck learning how to use it...it's wonderful but challenging. Some line-by-line handholding would be nice.

Thanks in advance.

---

### Post by meindian523 on 2007-09-01
What's the menu that comes when you boot the PC without using the Grub CD?
Also,please post ```
sudo fdisk -l
``` from the Ubuntu Live CD.

Have you tried re-installing grub?Lookit here for a tutorial:

[How-To install Grub from Ubuntu Live CD.]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by gshyland on 2007-09-01
Thanks, I just followed the tutorial and it's fixed, dual booting happily again.
I don't know why I was having such trouble :)

---

### Post by gshyland on 2007-09-01
Specifically I did the following in case others have the same issue:

sudo grub

grub> find /boot/grub/stage1

grub's response: (hd0,2)  <drive and partition vary depending on your layout>

grub> root (hd?,?) <plug in the drive & partition from the line above>

grub> setup (hd0)

...following the tutorial to the letter, which usually works :)
Thanks again.

---

