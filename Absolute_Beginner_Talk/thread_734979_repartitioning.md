---
title: "repartitioning"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by mahela007 on 2008-03-25
HI.. I have a 40 GB hard disk (I know.. ...veery small) and I also have a dual boot sytem of windows XP and Ubuntu.
The windows partitioon is about 19 gb
and the ubuntu partition is something like 8 GB
When I installed ubuntu I somehow manged to screw up the installation (no worries.. ubuntu and Xp are working fine) and now i am left with a unassigned part on my hard disk. Its about 4 BG. I booted form the live cd and launched Gparted.
I have attached a screen shot of what gparted looked like at this point.

**MY QUESTION**

How do I assign the unassigned part to the ubuntu partition so that the size of the ubuntu partition will be larger?

---

### Post by Oldsoldier2003 on 2008-03-25
> **mahela007 said:**
> HI.. I have a 40 GB hard disk (I know.. ...veery small) and I also have a dual boot sytem of windows XP and Ubuntu.
The windows partitioon is about 19 gb
and the ubuntu partition is something like 8 GB
When I installed ubuntu I somehow manged to screw up the installation (no worries.. ubuntu and Xp are working fine) and now i am left with a unassigned part on my hard disk. Its about 4 BG. I booted form the live cd and launched Gparted.
I have attached a screen shot of what gparted looked like at this point.

**MY QUESTION**

How do I assign the unassigned part to the ubuntu partition so that the size of the ubuntu partition will be larger?

the easiest way wold be to download the [GParted Live CD]("http://gparted-livecd.tuxfamily.org/"), then shift your patitions and grow the Ubuntu partition. be sure to back up your critical data before messing with the partitions.

---

### Post by mahela007 on 2008-03-25
cant i use the partitioner on the ubuntu live cd?

{ what if i just format is as ext3? will that make ubuntu recognize it in its file browser and allow me to store files on it?}

---

### Post by seshomaru samma on 2008-03-25
you can use the live -cd
you'll have to shrink sda2 (the logical partition containing the small NTFS, SWAP and the partitioned space)
it should result in a new partitioned space  not connected to anything which you can either add to sda3 (your ubuntu) or format as a new partition (ext3)
if you use a new partition you will have to mount it before you can use it (see [here]("http://www.psychocats.net/ubuntu/mountlinux"))

---

### Post by forrestcupp on 2008-03-25
If you want to resize your Ubuntu partition to use the extra space, you'll have to unmount it first.  That's the beauty of GParted LiveCD.  It's made for this stuff so it doesn't mount anything whereas Ubuntu LiveCD is made for other purposes, so it mounts everything.

---

### Post by logos34 on 2008-03-25
> **mahela007 said:**
> cant i use the partitioner on the ubuntu live cd?

{ what if i just format is as ext3? will that make ubuntu recognize it in its file browser and allow me to store files on it?}

Yes you can use the gparted on the ubuntu live cd--it can handle growing the partitions to the left. It takes a while though (as opposed to expanding to the right which is very quick).

Or make a separate ext3 partition like you say...make symlinks to it in home.  (-->'storage', whatever). 

Personally, if it were me I'd probably just delete swap, shrink the extended partition down all the way, then make a new swap right after it, and then grow root to the left to reclaim free space.  Edit swap line in fstab afterward.

---

### Post by mahela007 on 2008-03-25
but i thought i already had some unused space? (the grey area in the screen shot)

---

### Post by mahela007 on 2008-03-25
can anyone explain what "mounting " and "unmounting" is?
I'm a complete newbie when it comes to making partitions and stuff

---

### Post by meindian523 on 2008-03-25
Mounting basically means attaching(or linking) a partition to a folder under /media(usually) so that you can double click the folder and access the data on that partition.This is a very basic explanation,there are many more options with mount.See ```
man mount
```

Umounting means the exact opposite,as in it delinks the folder from the partition so you can no longer access/write data from/to the partition by just double clicking the folder.You need to mount any partition before you can access/write data from/to the partition depending on permissions,of course.See ```
man umount
```

---

### Post by seshomaru samma on 2008-03-25
> **mahela007 said:**
> but i thought i already had some unused space? (the grey area in the screen shot)
you do, but it is attached to your NTFS partition, if you want to make it a part of an ext3 partition you have to move it.
Mounting means you can access the partition, but you cant mount and resize in the same time, thats why you need to unmount. However with a Live CD you are okay because ,as far as I know, it doesn't mount the partitions by default.

---

### Post by Victormd on 2008-03-25
> **mahela007 said:**
> but i thought i already had some unused space? (the grey area in the screen shot)

You currently have 2 logical partitions (Sda1 with XP and Sda3 with Ubuntu) and one extended partition (containing Sda5 + blank partition + swap). What do you use Sda5 for? Backup? If so, then I would:
1. leave Sda1 and Sd5 untouched;
2. delete the swap partition (Now you'll have one 5Gb partition unused);
3. create the swap partition on the beginning of the free space (~512Mb) and edit swap line in fstab (replace sda6 for sda# where # is the new number assigned to the partition).
4. shrink your extended partition to accommodate ONLY your 5Gb backup partition and the swap partition;
5. grow your sda3 partition to the left.

Note: you can have only 4 (or 5 - not sure) logical partitions, that's why you SOMETIMES need the extended partition. No matter how many partitions you have INSIDE an extended partition, it is still seen as only 1 logical partition, thus, you can have more than 4 (or 5) partitions. Your ubuntu partition is a logical partition, so you can only grow with "logical partition space" and that's why you have to shrink your extended partition. You will NOT be able to grow your linux partition into the extended partition

---

### Post by mahela007 on 2008-03-25
ok. thanks...

---

### Post by mahela007 on 2008-03-26
what is fstab and how do i edit it?
You currently have 2 logical partitions (Sda1 with XP and Sda3 with Ubuntu) and one extended partition (containing Sda5 + blank partition + swap). What do you use Sda5 for? Backup? If so, then I would:
1. leave Sda1 and Sd5 untouched;
2. delete the swap partition (Now you'll have one 5Gb partition unused);
3. create the swap partition on the beginning of the free space (~512Mb) and edit swap line in ***_[COLOR="Navy"]fstab[/COLOR]_*** (replace sda6 for sda# where # is the new number assigned to the partition).
4. shrink your extended partition to accommodate ONLY your 5Gb backup partition and the swap partition;
5. grow your sda3 partition to the left.

---

### Post by meindian523 on 2008-03-26
fstab is **f**ile**s**ystem **tab**le found in /etc

To edit,press Alt+F2,then ```
gksudo gedit /etc/fstab
```

---

### Post by mahela007 on 2008-03-27
ok!! thanks for helping me out!

---

### Post by meindian523 on 2008-03-27
Is your issue resolved?

---

### Post by mahela007 on 2008-03-27
i didnt do it yet. i want to wait a while to see how soon i run out of disk space. lol

---

