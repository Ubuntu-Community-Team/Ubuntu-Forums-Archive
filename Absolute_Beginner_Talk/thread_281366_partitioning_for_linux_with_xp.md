---
title: "partitioning for linux with xp"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-10-20
I have windows XP running on my computer 
I want to install KUBUNTU as a multiboot operating system
Prsently my hard disk has one primary partion(fat 32,2GB) and several logical drives in one extended partion.
windows Xp is on one of these logical drives.

There is sufficient space on my hard disk


Please let me know 

1) Can the linux partitions be all logical drives in the extended partition

or 

1) I have to reduce the extended partition's size and make primary partition/partitions for linux


2) How may logical drives/partitions are ideal for LINUX for occasional usage

---

### Post by aysiu on 2006-10-20
Reading this may answer some of your questions:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by dhawald3 on 2006-10-21
> **aysiu said:**
> Reading this may answer some of your questions:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

thanks
but the page does not give info about
if linux can be installed on a logical drive or if it needs a primary partition.

---

### Post by Kateikyoushi on 2006-10-21
It can be installed on logical partition as well.

---

### Post by nyinge on 2006-10-21
> **Kateikyoushi said:**
> It can be installed on logical partition as well.
So, you mean GRUB would take care of the rest?  Because on windows, I thought it can be only booted off from an active primary partition.  If I'm not making sense, please disregard this post.  :mrgreen:

---

### Post by hyper_ch on 2006-10-21
nyinge: I would recommend you the following:

1.) Make a backup of your data
2.) Get a hold of Partition Magic (I know, it's win software but I tend to think it's so intuitively that you can't really f*** anything up)
3.) With Partition Magic resizes you partitions (if needed) and make one big chunk of free/empty diskspace on the hard drive
4.) Install you flavour of Ubuntu into that free/empty diskspace Ubuntu will partition it to automatically...
however you can also partition it yourself from the gui partition tool within the ubuntu installatin procedure
You will need:
- a swap partition (recommended 2x the size of your ram)
- a root partition (where "/" is going to be)
(- a home partition (where "/home" is going to be --> not necessary but recommended)

For the swap partition select as filesystem just swap and for the others I recommend ext3.

---

### Post by Kateikyoushi on 2006-10-21
Yes, grub takes care of the rest.
Check out this grub menu which loads 100+ OS. ;) [LINK]("http://www.justlinux.com/forum/showthread.php?threadid=143973")

---

### Post by nyinge on 2006-10-23
Thanks, Sjau and Kateikyoushi.  GRUB indeed is a really powerful boot loader.  I have always installed OS's in primary partitions.  It's great to know that Linux can be installed in a logical partition as well.  Now, I can have more than 4 OS's on my disk.  :)

---

### Post by gn2 on 2006-10-23
> **nyinge said:**
> Thanks, Sjau and Kateikyoushi.  GRUB indeed is a really powerful boot loader.  I have always installed OS's in primary partitions.  It's great to know that Linux can be installed in a logical partition as well.  Now, I can have more than 4 OS's on my disk.  :)

With Parallels or VMWare server you could even run them two at a time.....

The most I know of is a friend who says he "needs" eight OS's.
He just can't make a decision methinks!

---

### Post by apoch on 2006-10-23
If you don't want to mess with your partitions and have fifty bucks, buy a second hard drive. Install it as the master drive and install ubuntu. Then edit /boot/grub/menu.lst and add

title    Windows XP
         map (hd0,0) (hd1,0)
         map (hd1,0) (hd0,0)
         root (hd1,0)
         makeactive
         chainloader +1

This tells Windows it's the primary drive even when though your linux drive is.

---

### Post by steve.horsley on 2006-10-23
A couple of cautions:

The graphical installer only offers 3 options:
* erase the disk
* use the remaining free space
* shrink windows and then use the free space
For more custom partitoning, such as creating partitions that only occupy some of the free space, you need the "alternate" installer. You will want to create:
* A root (/) partition of 5+ Gig for the system
* A swap partition of maybe 1 Gig for virtual memory
* possibly a /home partition for users home directories (equiv. to My Documents). This allows a complete re-install of the OS without losing user data.

GRUB relies on files in /boot/grub on the Linux system partition. Deleting that partition kills grub. This matters when you delete/upgrade Ubuntu.

---

