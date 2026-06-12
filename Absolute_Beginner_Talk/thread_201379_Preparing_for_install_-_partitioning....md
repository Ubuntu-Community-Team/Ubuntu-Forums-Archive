---
title: "Preparing for install - partitioning..."
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by DizMan on 2006-06-21
#-o 

Hi.

While downloading Ubuntu i'm preparing my system for the install.

Here's my problem:

When I got my pc I partioned the disk into 2 and installed Win XP in the primary partition. Since I've had lots of "fun" - especially when my cpu (P4-3,2) crashed permanently.

I got a new CPU - and a new HD as well. The new HD was now placed as the primary disk and also partitioned in 2. Again I installed Win XP in the primary partition, so that I had 2 Win installs (I could just switch Win XP by switching the HD cable).

Well, I've now deleted all data on the "old" Win drive (D:\). This partiotion is now intended for Ubuntu. But I can't seem to delete that it was a system partition. After formatting, using Norton Partition Magick, swearing in several languages and googleing I still have got an undeleteable folder called System Volume Information.

What to to? Will this be fixed by the Ubuntu installer?

Hope to hear from you soon!

All the best...
/Lars

---

### Post by Eidar on 2006-06-21
Boot into dos mode and format from there, or boot using the WinXP CD and format from the resque mode. That should be it!

---

### Post by Jasper Houtman on 2006-06-21
Completely remove the second partition with partition magic.
Then boot up the ubuntu install cd, and let the partition tool do the partitioning for you (select automatically partition free space).

Do not create the partitions you need in partition magic!!! I tried this and it didn't work. Besides letting the installer do it for you is much easier.

---

### Post by Jasper Houtman on 2006-06-21
[QUOTE=Eidar]Boot into dos mode and format from there, or boot using the WinXP CD and format from the resque mode. That should be it![/QUOTE]

Bad idea. You need a swap partition for Ubuntu!
Just delete the partition and let the ubuntu's installer configure everything for you. Besides if it was created by XP it's either an fat or an NTFS partition.

Linux won't accept NTFS, and installing on fat will make it much slower (asuming it will work at all).

---

### Post by DizMan on 2006-06-21
Hi again.

Thanks for the quick answers. I think you gave me the solution. One question though. The partition intended for Ubuntu currently have the drive letter D.

When I use that for Ubuntu what will happen with my partitions that succeed D - i've got E and F. I would like these drivenames to remain due to a bunch of links to files on these drives...

---

### Post by jimrz on 2006-06-21
[QUOTE=DizMan]Hi again.

Thanks for the quick answers. I think you gave me the solution. One question though. The partition intended for Ubuntu currently have the drive letter D.

When I use that for Ubuntu what will happen with my partitions that succeed D - i've got E and F. I would like these drivenames to remain due to a bunch of links to files on these drives...[/QUOTE]

you could, using partition magic and before your ubuntu install, put a small FAT32 (useful for sharing data between ubuntu and win) and label it as "/D". then when you do install select "manual partition" and set up your / + swap + i recommend having a separate /home partition (this will prove useful further down your ubuntu road)

welcome and good luck

---

