---
title: "Can't decide on disk partitioning"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by neptune on 2006-10-12
Hi everyone,

I just upgraded my computer and trying to plan a Ubuntu 6.06 installation.

However, I'm stuck at trying to determine how best to partition the disks I have:
1x 160gb SATA
1x 200gb IDE

To be honest, I haven't decided what role this system will have. It's going to become my daily-use machine: web, email, music, video, dvd/cd writing, etc.
Apart from that, it will need to communicate with my Windows print server and shared folders (also on Windows).
Eventually, the plan is to migrate these two functions over to this system on Ubuntu.

My wife has a Windows laptop that requires printing and shared storage space. And I have the aforementioned Windows system (which is my current daily use machine). The Windows desktop has just 2x 13gb IDE and 1x 4gb SCSI drives.

I'm seeking some advice/recommendations on how to partition for Ubuntu.

Your assistance is greatly appreciated.

Thanks!

---

### Post by bulldog on 2006-10-12
Which drive you want to use for Ubuntu??

Okay,you can make a / [root] partition of about 10GB.
Make a swap about twice your fysical RAM ,but not bigger as 2GB.
The rest of the space you make /home.

---

### Post by neptune on 2006-10-12
I want to try and optimize space on both drives as much as possible. Using both drives is fine with me, either individually partitioned or using LVM or a combination.

I prefer not to have an entire drive just sitting not doing anything. If need be, I can replace the 200gb IDE with a spare 60gb SATA.

---

### Post by bulldog on 2006-10-12
You don't have to use a whole drive for Ubuntu.
Make your /home as big as you want that won't affect Ubuntu at all.

But when you want to migrate data between Ubuntu and windows,a FAT32 partition should be handy.

---

### Post by neptune on 2006-10-12
Alright well I spent some time today researching this topic.

Here's what I've come up with:

swap - 2 GB (system has 1GB physical RAM)
boot - 150 MB
root - 5 GB
tmp - 1 GB
usr - 25 GB
opt - 25 GB
var - 25 GB
home - 30 GB
media - 100 GB
fat32 - 30 GB
export - 30 GB *

total: 273.15 GB

* Regarding the export or srv partition: what filesystem does it need to be if I use SAMBA to share files across my Windows network? Does this need to be FAT32 or can I use XFS or ext3?

How does this scheme look? I'd appreciate some constructive critique / suggestions / comments.
Keep in mind that I'm a newbie and trying to learn so please be gentle. :)

Thanks!

---

### Post by lha on 2006-10-13
> **neptune said:**
> Alright well I spent some time today researching this topic.

Here's what I've come up with:

swap - 2 GB (system has 1GB physical RAM)
boot - 150 MB
root - 5 GB
tmp - 1 GB
usr - 25 GB
opt - 25 GB
var - 25 GB
home - 30 GB
media - 100 GB
fat32 - 30 GB
export - 30 GB *

total: 273.15 GB

* Regarding the export or srv partition: what filesystem does it need to be if I use SAMBA to share files across my Windows network? Does this need to be FAT32 or can I use XFS or ext3?

How does this scheme look? I'd appreciate some constructive critique / suggestions / comments.
Keep in mind that I'm a newbie and trying to learn so please be gentle. :)

Thanks!
I think you are planning on creating too many partitions - way too many. You'll run out of space on one or two partitions and still have many partitions almost empty. Keep it simple is my advice. Swap, root and home is usually enough.

---

### Post by luckylucky on 2006-10-13
Ok, I'll be "gentle", since you are a newbie.  What is suggested here is definetly not a good idea simply for the reason that you'll end up wasting large portions of your hard drive for unnecessary space.

Though I certainly split up my hard drives into a number of partitions (and for good reasons) since you mentioned that you are simply intending on using your computer for basic home use then I'd recommend the "KISS" approach of keeping it simple.

If you plan to have Windows coexisting on your computer then install it first, then with a tool like GParted (download the iso from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) ) shrink (resize NTFS) your windows partition to about 20 gigs, then make a 1 to 2 gig "swap" partition, then a 20 gig "/" (ext3) partition for your linux, then the rest of your hard drive format it to FAT32 and call it "/storage" so you have a place to keep your files accessible to both windows and linux.  If you have no plan for using windows then just ignore that partition.  Most of my computers basically have variations of this partitioning theme.

Of course, depending on what you are intending on doing, you might make different partition schemes, but if you are a newbie, or just have basic needs, then the above partition scheme should be adequate for you.  I hope that this helped.


> **neptune said:**
> Alright well I spent some time today researching this topic.

Here's what I've come up with:

swap - 2 GB (system has 1GB physical RAM)
boot - 150 MB
root - 5 GB
tmp - 1 GB
usr - 25 GB
opt - 25 GB
var - 25 GB
home - 30 GB
media - 100 GB
fat32 - 30 GB
export - 30 GB *

total: 273.15 GB

* Regarding the export or srv partition: what filesystem does it need to be if I use SAMBA to share files across my Windows network? Does this need to be FAT32 or can I use XFS or ext3?

How does this scheme look? I'd appreciate some constructive critique / suggestions / comments.
Keep in mind that I'm a newbie and trying to learn so please be gentle. :)

Thanks!

---

### Post by luckylucky on 2006-10-13
Also... since you have two physical hard drives you could simply make one for linux, the other for windows, but make sure that on one of them you make a FAT32 partition to be able to share data between windows & linux.

Good luck!

---

### Post by gn2 on 2006-10-13
Generally the usual way that is suggested to install a dual-boot system involves overwriting the Master Boot Record of the Windows hard drive.

On one hard drive this is pretty much unavoidable.

HOWEVER:

If you are dual-booting with TWO hard drives it is not necessary to write Grub over the MBR if you can access a "Boot Device Selection Menu" by pressing F8
(or whatever key depending on BIOS)

You can keep both installations entirely separate and avoid a host of problems later on.

To do it this way:

Disconnect the Windows drive and install Ubuntu and Grub on the second drive. Reconnect first drive after installing Ubuntu.

Windows on master, Ubuntu & Grub on slave if using two IDE drives.

(This method will also work on SATA drives, or a mix of SATA & IDE)

Press F8 (or whatever key depending on BIOS version) at boot time to bring up the Boot Device Selection Menu.

Choose OS by selecting which drive to boot from.

Select desired default OS by re-arranging boot order in BIOS.

Only need to press F8 to select non-default OS.

Re-boots are as quick as using traditional Grub-in-MBR option.

Always disconnect other OS's drive if re-installing.

This process will also work for adding Windows to a Ubuntu system

If you take this option you will never have any issues with Grub menu lists or MBR corruption.

Grub on my MBR was worse than any virus I ever had.

Access to files on either drive can be configured later on, once you've got a safe installation organised.

Just keep your files on a different partition from your OS and you'll be fine, what you are proposing looks way too uneccessarily complex.
.

---

