---
title: "Two Feisty installs/remove one and resize the other"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-11-03
To make this short as possible, I did have Gutsy but it did not work for me and I installed a fresh Feisty 7.04 and had it almost tweaked perfectly but I messed up xorg.conf and before I could repair it right, I installed a new Feisty install on same hard drive. 

Since my first install has several major things added like Beryl.Wine, email and browsers configured right, I want to keep that one. I did try with gparted ie gnome partition manager and was able to get rid of the second install and deleted the partition and it was unallocated space but I could not resize my first install of Feisty. 

That sent me into more quirks as I could not boot into any OS because of an error 22, obviously the menu.lst from the second install was gone and grub was confused. 

So I installed Feisty again and have two installs of Feisty on the same HD and I want to get rid of the second and keep the first and resize the partition to occupy the full disc. 

Here is output 
Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1784    14329948+  83  Linux
/dev/sdb2            3343        3649     2465977+   5  Extended
/dev/sdb3   *        1785        3342    12514635   83  Linux
/dev/sdb5            3494        3649     1253038+  82  Linux swap / Solaris
/dev/sdb6            3418        3493      610407   82  Linux swap / Solaris
/dev/sdb7            3343        3417      602374+  82  Linux swap / Solaris

Partition table entries are not in disk order
steve@NVFC:~$ blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D3-0C09" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" 
/dev/sda3: TYPE="ntfs" 
/dev/sda5: UUID="923c51e4-d776-41e7-92ab-508039d02e80" TYPE="swap" 
/dev/sdb1: UUID="c11e93d7-c35e-44e0-86e3-555d238ecff1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="5d74751e-a0e5-4916-af78-d0de7ddb077a" TYPE="swap" 
steve@NVFC:~$

---

### Post by yogo on 2007-11-03
Any ideas?

---

### Post by mdpalow on 2007-11-03
you originally posted this message in another thread where I explained how to use 'gparted.' Recommend you go back and look at that as it will explain what you can do.

---

### Post by yogo on 2007-11-03
> **mdpalow said:**
> you originally posted this message in another thread where I explained how to use 'gparted.' Recommend you go back and look at that as it will explain what you can do.
  and I also deleted it from that thread as sometimes it is better to start a new thread.

I waited two hours and then removed it from there are started this.

If you are talking about your answer above the post of mine, I did read that, HOWEVER I am not able to resize through gparted, at least not my original install, the second install, I can resize or delete but that is not the one I want to resize, even if that space in unallocated, I can not resize so my answer was not give there.

---

### Post by Duck2006 on 2007-11-03
Use this one 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Not the one in ubuntu.

---

### Post by overdrank on 2007-11-03
> **yogo said:**
> 
Here is output 
Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1784    14329948+  83  Linux
/dev/sdb2            3343        3649     2465977+   5  Extended
/dev/sdb3   *        1785        3342    12514635   83  Linux
/dev/sdb5            3494        3649     1253038+  82  Linux swap / Solaris
/dev/sdb6            3418        3493      610407   82  Linux swap / Solaris
/dev/sdb7            3343        3417      602374+  82  Linux swap / Solaris

Partition table entries are not in disk order
steve@NVFC:~$ blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D3-0C09" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" 
/dev/sda3: TYPE="ntfs" 
/dev/sda5: UUID="923c51e4-d776-41e7-92ab-508039d02e80" TYPE="swap" 
/dev/sdb1: UUID="c11e93d7-c35e-44e0-86e3-555d238ecff1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="5d74751e-a0e5-4916-af78-d0de7ddb077a" TYPE="swap" 
steve@NVFC:~$

HI and please correct me if I am wrong but if sdb1 is the partition that you are wanting to keep I don't believe you will be able to resize it because everything after that is on a extended partition and that is why gparted will not let you resize lager. :-k

---

### Post by yogo on 2007-11-03
> **overdrank said:**
> HI and please correct me if I am wrong but if sdb1 is the partition that you are wanting to keep I don't believe you will be able to resize it because everything after that is on a extended partition and that is why gparted will not let you resize lager. :-k



I believe you are right.  sdb1 is the one I want to keep, that makes sense as to why gparted would not let me resize it.

I am assuming the other gparted linked above by duck2006 will not work as well.

What do I need to do to get around this?


TIA

---

### Post by Duck2006 on 2007-11-03
Yes you can do with the live CD read this

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

It just means that you will be resizing with in the extended Partition, if you want to add it to the logic partition you will have to delete the extended partition and resize the logic partition. Don't forget to make a swap partition.

---

### Post by yogo on 2007-11-03
Thanks Duck, I do have gparted on CD so I am going to give it a try.

I am a little confused as there are already three swap partitions, what worries me is that I may get rid of menu.lst that points to the wrong OS.

Will gparted give me the options to repair grub etc?

---

### Post by yogo on 2007-11-03
I used gparted live CD and was able to shink the second install to about 2.5 gigs so I freed up 10 gigs that are now unallocated that I would like to add to the first install of Feisty but still I can not resize the first partition bigger although gparted live CD at least has the option available to resize but it is as large as gparted will let me have it.

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1784    14329948+  83  Linux
[COLOR=Red]/dev/sdb2            3343        3649     2465977+   5  Extended[/COLOR]
/dev/sdb3   *        1785        2099     2530237+  83  Linux
/[COLOR=Red]dev/sdb5            3494        3649     1253038+  82  Linux swap / Solaris
/dev/sdb6            3418        3493      610407   82  Linux swap / Solaris
/dev/sdb7            3343        3417      602374+  82  Linux swap / Solaris

[COLOR=Black]Out of the partitions in red, which ones can I feel safe to delete?

I only need one swap but which one? Also I do not think I need the extended partition...?

TIA
[/COLOR][/COLOR]

---

### Post by Duck2006 on 2007-11-04
Leve the last swap partition on there that way you can resize your / partition. You can reinstall grub again if it's point to the wrong menu.lst

---

### Post by yogo on 2007-11-04
For some reason this is seeming next to impossible.

It is like trying to move a three hundred pound woman that refuses to budge or even sing.

I can not move/resize my original partition at all, I have read tutorials and I was going to try to "COPY" the unallocated space and "PASTE" it into the partition I want to enlarge.

I can only shrink the first partition, not make it bigger.

Out of frustration, I decided to just do a fresh install and allow the new install to occupy the entire disc.

Now I will have to redo everything.

I would like to know what I am missing so that I can move these partitions etc, but the was it was going it would be equivalent to me not being able to physically carry one bedroom from one area of the house to another.

Advice and knowledge is always appreciated.

Thanks

---

