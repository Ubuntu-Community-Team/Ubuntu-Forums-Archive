---
title: "Partitioning: Question of Size"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by unconquerable on 2006-08-07
I have a 80 gig harddrive. I just installed my Windows XP partition which is 15 gig.  There is also a 1 gig "QuickPlay partion which allows me to play dvds without booting.

My question is how big should my 3 partitions in linux be.  There are three right?  I have 512 of ram if that matters for swap size.  

I wish to give ubuntu 10-15 gigs and leave the last 45 or so gigs for fat 32, so things can be shared between the two.

---

### Post by nathano on 2006-08-07
Really, you need a minimum of only one partition for Linux (mounted as "/"). A swap partition is always a good idea, too. Some people advocate using different partitions for different mount points, but for your average desktop system, I find that to be more headache than it's worth. Of course, if you're setting up a multifunction, Internet-exposed server, you might want to get fancy.

Personally, since you've got so much space to work with, I'd make a swap partition of a full gig and a regular partition of whatever size you want for Ubuntu. Treat it like your C drive, except it's for Linux.

Personally, under Windows, I prefer to make a partition for C and a separate partition that I set up just for the pagefile. It's a rough equivalent to the Linux setup outlined above. And if you can put the pagefile (or swap partition) on a separate drive... even on a separate controller, if you can... then all the better!

---

### Post by arjun.shankar on 2006-08-07
The most sensible option is to have about 1G of space swap (it's generally kept at double the RAM), and leave to rest as the "/" partition. That way, it wouldn't matter which way your installation grows, applications (they fill up directories other than "/home"), OR data (fills up the "/home" directory).

I'm guessing by 'three' you meant swap,"/" and "/home". You can have more, or less, depending on your level of confidence on what you are going to fill up faster.

---

### Post by arjun.shankar on 2006-08-07
Oops! nathano just replied What a waste of keystrokes... ;)

---

### Post by unconquerable on 2006-08-07
It is not a waste of keystokes, it is confirmation for me.  Thanks to you both.

---

### Post by anaconda on 2006-08-07
What is a QuickPlay partition? newer heard that before.

And I always play DVD:s vithout booting..

And it is a matter of taste do you make a swap-partition or a swap-file to your ubuntu partition...Whatever.. separate swap-partition is better if you install several linuxes, then all of them can use the same swap..

---

### Post by unconquerable on 2006-08-07
Ok more problems

Here is my current config (order as it appears):

1: WinXP Partition (15 gb)
2: Swap Partition  (should this be primary or ext?)1 gb
3: / parition (primary) (10 gb)
4: Trying to use rest of the space as a fat32 partition but it says when I click "new partition" that I can only have 4 primary partitions and I should make an extended one that can hold multiple partitions.  Where should I put the fat32 partition then
5: Quickplay (1 gb)

---

### Post by anaconda on 2006-08-07
The maximum number of primary partitions is 4, so you should make 1 extended partition (which is primary) which can be divided to as many logical partitions as you wish.

Swap and your fat32 partitions can very well be logical partitions. (as can / , but let it be primary if possible..)

so my suggestion:
primary1: winXP 15GB
primary2: ubuntu / 10GB
primary3: QuickPlay 1GB
primary4: the rest go to an extended partition which is divided to:
  logical1: Swap 1GB 
  logical2: fat32 partition

Actually I would make the ubuntu partition bigger and forget the fat32 partition. because windows can read/write to ext3 partitions by using fs-driver..

---

### Post by unconquerable on 2006-08-07
I setup my partitions as stated above... but now I am confused the installer still does not recognize which partition to use for "/" how do I "tell it".

---

### Post by unconquerable on 2006-08-07
I have been messing around with this for a while in my free time but the install does not know where to put the "/" how to I label it or point it to the correct partition?

---

### Post by mlind on 2006-08-07
How about using LVM instead? If you get second thoughts about partition sizes (which usually always happens), you can always resize them.
Just put /boot on separate partition and outside of LVM.

---

### Post by unconquerable on 2006-08-07
LVM?  I do not know what that is.

---

### Post by mlind on 2006-08-07
> **unconquerable said:**
> LVM?  I do not know what that is.

This should provide indepth information [http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)


Simple usecase example from yesterday:

My $HOME partition was getting too small again. Normally I would need to create new partition with enough free space this time, move files between partitions and fix mountpoints.
With LVM I just umounted my /home, expanded its LV with 5GB's, ran resize2fs (so that partition expands to the size of LV) and mounted partition back. Now it's 5GB's bigger and no additional hassle.

---

### Post by unconquerable on 2006-08-07
Sound complicated, all I want to do is get Ubuntu to recognize the partition I made for it.

I normally let Ubuntu Install Partition for me, WHAT DO I NEED TO DO TO GET IT TO THINK THE PARTITION I MADE FOR IT IS "/"

---

### Post by mlind on 2006-08-08
> **unconquerable said:**
> Sound complicated, all I want to do is get Ubuntu to recognize the partition I made for it.

I normally let Ubuntu Install Partition for me, WHAT DO I NEED TO DO TO GET IT TO THINK THE PARTITION I MADE FOR IT IS "/"

There's something wrong with your keyboard?

You just have to mount it as root partition. define it on /etc/fstab and also change it on /boot/grub/menu.lst.

---

### Post by anaconda on 2006-08-08
When installing ubuntu go to partition manually (or whatever it was..)
then just select the partition you intend to be "/" and select it's mount point to be "/".

After thet you can continue. You just have to mark one partition to be "/" otherwice the install can't continue.

---

### Post by Titus A Duxass on 2006-08-08
Nathano was right you need only one partitiion - But if you set up a / , /home and a swap you can reinstall ubuntu as often as you like without deleting your data (as long as you do not format the /home).

I would have 8 - 10 gb for the root (/)
and 50% of the remaining for home and the rest for sharing.

---

### Post by Ludwig7666 on 2006-08-08
My answer to this would be. Go out and by a exturnal HDD. :P slit the inturnal HDD to linux and windows then have the exturnal as whatever you want. They are I believe all already in fat32. Also a nice thing about them is that you can place them onto any USB abled computer to use whatever is on it. :P Just like that. ;)

---

### Post by az on 2006-08-08
> **unconquerable said:**
> Sound complicated, all I want to do is get Ubuntu to recognize the partition I made for it.

I normally let Ubuntu Install Partition for me, WHAT DO I NEED TO DO TO GET IT TO THINK THE PARTITION I MADE FOR IT IS "/"

Manual partitioning is complicated.  That's why the installer can do it for you, automagically.  You don't need to decide how big your swap is and so forth...

As for a home partition, a lot of the time, your configurations are borked and you need to remove them from your home drive anyway.  It's simpler to just back up your data the conventional way.

---

