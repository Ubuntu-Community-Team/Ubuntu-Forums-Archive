---
title: "Grub menu diappeared from dual boot-can't boot ubuntu"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by newmo on 2006-09-03
Hi sometime last week the the grub menu disappeared at boot-up meaning that I have no choice but to boot into windows or use a Live CD.

My girlfriend reported she had some usual window appear at shutdown which kept rebooting or something and she "finally got rid of it".  My only guess is it was something to do with msconfig (I might have gone into it to get rid of system tray rubbish earlier).

Whatever it was the Grub menu has now gone and I am locked out of Ubuntu.


I have been looking hard at some solutions to this at threads such as this 

[http://www.ubuntuforums.org/showthread.php?t=22435](http://www.ubuntuforums.org/showthread.php?t=22435)

(But being a noob I am not even sure they aren't answers to a different problem)

There seem to be three approachs - I've had no luck yet obviously.

1) using the grub command line

find /boot/grub/stage1

This returns Error 15 file not found.

I can see it (stage1 file in the grub directory)with Knoppix/Puppy or whatever but thats as far as I get with this method.


I have tried to guess the location(I think I used hd1,0) and continued with the root setup and quit commands and it even told me I had been sucessful but when I rebooted still no grub menu.  it still goes straight to XP.

2)Using the Breezy Install CD

(I am at a disadvantage here as I have never installed Ubuntu...someone did it for me.)

I chug away ok then get to manual partition.  I change the mount points (think I did it correctly hdb1=/boot for example...) but I can't get any further. I go to install grub and it just sends me back to the partioner  and I get stuck in an endless loop.  I haven't got to Part 4 of the instructions in the Wiki yet.

3) This involves the chroot command and mounting devices to a new directory

Instructiona are something like sudo mkdir /mnt/root

then mount /dev/xxx /mnt/root
chroot /mnt/root /bin/bash

This comes unstuck as well.  In Puppy I get 

chroot: cannot execute /bin/bash: No such file or directory

This is the output of fdisk -l using Puppy

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          12       96358+  83  Linux
/dev/hdb2              13         105      747022+  82  Linux swap / Solaris
/dev/hdb3             106        4968    39062047+  83  Linux
/dev/hdb4            4969        7605    21181702+   5  Extended
/dev/hdb5            4969        7605    21181671   83  Linux

Disk /dev/sda: 2091 MB, 2091908608 bytes
64 heads, 63 sectors/track, 1013 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1014     2042848    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 63, 63) logical=(1013, 21, 20)
sh-3.1# 



If anyone knows what I'm doing wrong here I'll be grateful for some advice.

(Failing that: I can see my files in ubuntu using a LiveCD but I can't copy them to disk because I don't have permission.  Is there a noob-friendly tutorial on how to rescue my ubuntu docs and files using a Live CD?  Is the How to Mount a Linux Partition tutorial the right thing I should be looking at or am I looking in the wrong direction?)

---

### Post by davmac on 2006-09-04
Have a read of this thread about how to restore grub - [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

Hope this helps,

Dave Mac

---

### Post by newmo on 2006-09-04
Thanks for your reply.

Think I will try and rescue the data and reinstall.

The 'solution' here doesn't work for my machine...not with me at the controls anyway.

(I really wish I didn't have to reinstall...I was having one last look for a solution when I saw your reply)

---

