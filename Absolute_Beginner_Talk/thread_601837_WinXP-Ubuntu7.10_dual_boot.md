---
title: "WinXP-Ubuntu7.10 dual boot"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by hydraconsole on 2007-11-03
Hi,

I've been using Windows since DOS began eons ago. I'm very new to Linux. I am currently using WinXP Pro on a machine with two NTFS partitions on a single HD. I want to know how to install Ubuntu on the second partition.

I can back up my files from the second partition to the first one so that the 2nd partition can be used for Ubuntu alone.

I've read the other threads about partitioning and I got lost on the manual part of the installation.

Any help would be greatly appreciated.

Thanks in advance

---

### Post by jake16424 on 2007-11-03
so long as there isn't any information that you still need on the second partition, just throw the disk in, hit ESC or whatever allows you to boot from the cd, after ubuntu starts up click install then answer all that crap, at about step 4 there is a partition manager and from there you select the partition of the drive you want to use. 

=-)

good luck.

---

### Post by gate on 2007-11-03
The install will guide you up to the point where you select a drive to install it on. At that point, you need to select the "manual" option. Among that dialog you can "delete" the NTFS partition you want to erase, and "Create" TWO. The first one needs to be 1-2 Gigs, or if you have that much to spare, and the use as box should say "Swap". The second should be all the space that is left  in the unpartitioned space, and it should be used as EXT3 with a mount point of a single slash (/)

---

### Post by cuby on 2007-11-03
Last post got it right... but you should perform a backup of sensitive data, just in case.

---

### Post by Duck2006 on 2007-11-03
When you install and it comes to the partitioning just tell it what drive to use and to use the hole drive and it will do it for you.

---

### Post by ub9876 on 2007-11-03
i did it and it was easy.  run defrag 2 times before you do it. you need the iso stuff on CD
not DVD and select the burn item ,not just the copy option.

---

### Post by tw0shoes on 2007-11-03
uhh, make sure you select Manual when it asks, otherwise it'll write over everything.

---

### Post by hydraconsole on 2007-11-03
thanks guys. i'll try it as soon i finish downloading gutsy

wish me luck

i was able to borrow a cd-rom, downloaded alternate iso and burned it to cd. now using it. have a lot of questions though about using several programs and customizing it.

---

