---
title: "Secondary hard drive setup for linux"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2006-12-14
After trying out Ubuntu 6.06 for about 2 weeks on a dual boot, I am now sure I want to use Ubuntu as my primary operating system. 

My setup prior to linux was Windows XP and I had two hard drives. One was the operating system, programs, etc. The second drive was used as storage basically, I kept my mp3's, videos, school stuff etc on there.

Whats the best way to set up the same thing in linux? I know it is possible to mount an NTFS drive, is this recommended? Or should I format the drive for linux?

Obviously, the second choice would be more work, with having to copy everything back onto the drive after formatting, but in the long run it's really a small amout of effort.

What would be the ideal setup in this situation?

-Andrew

---

### Post by taurus on 2006-12-14
I would install Ubuntu on the first harddrive, wiping out Windows.  Then, mount the second harddrive and copy all your important stuff over to your $HOME directory or wherever else on the first drive.  Then, format the second harddrive to ext3 and use it as a storage.  That's the best way to do and there are other ways too...

---

### Post by indytim on 2006-12-14
Altreus12 welcome to the world of Linux and especially Ubuntu-Kubuntu.

How you set up your drives is strictly a matter of preference.  A couple of things to consider if you're doing it from scratch.

1.  You might want to consider FAT32 partition(s) for any parittions that need to share data BETWEEN Ubuntu and Windows.  If you go this route, be mindful of the filessize restrictions associated with FAT32.
2.  When you install The Linux system, you can designate partition locations for / , /home, /swap.  This will give you complete control over where things go upon install.  It's a good idea to put your /home on a different partition.  That way you won't loose the data should you decide to upgrade to a new Linux at a later date (ie going from dapper -> edgy) -- assumes you would wipe clean the original distribution.

I presently have 2 sata hd's in my box.  The first one is a 160G SATA.  Basically, that HD is used for my operating systems.  The second HD is used for data storage.  It's lineup is
sdb1 - NTFS 20 G 
sdb2 - FAT32 40G used for media share between Win - Lx
sdb3 ext3 Data 80G principal storage area for Linux data and media files
sdb4 - 30G Used for backups and setups for my LInux systems

I am currently triple booting to Win2k, Ubuntu - Dapper and, Kubuntu Edgy.

Hope all of this is of some help to you.

IndyTim

---

### Post by dwblas on 2006-12-14
It's a personal thing, but I would format the 2nd drive as ext3 and copy the files back because it is more reliable IMO.  As long as you don't have any Windows specific files, like exe's, you should be O.K.  If you have room, copy everything to your Linux partition first, test play some mp3s and see what happens.

---

### Post by Atreus12 on 2006-12-14
First off, I am ok with computers, but not exactly an expert.

My secondary drive is 120 GB, and I need 10 GB for windows, and the rest for linux. I would also be interested in putting my /home directory on the second drive (or maybe just a seperate partition of the primary drive?), but I don't really know how to do any of this.

What program should I use to create / manage partitions? Is it still possible to put my /home on the second drive since it is currently on my primary?

Edit: The windows partition on the second drive must be able to handle file sizes in excess of 5 GB.

---

### Post by taurus on 2006-12-14
The LiveCD comes with gparted that would allow to you partition your harddrives anyway you want to.  Do that first before you install Ubuntu but since you have to have Windows running on that machine as well, I recommend you install Windows first (after partitioning) and then Ubuntu after that...

---

### Post by indytim on 2006-12-14
With respect to adding new partitions, my recommendation is to use GParted.  I believe it is part of the LiveCD for Ubuntu.  There is also a "live" version for GParted at [http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php").

It can make things a bit easier if you set up you partitions beforehand to the install.

Just a side note, I consider having Live versions of the operating system, GParted and Super grub part of my "essential" tookit.

IndyTim

---

### Post by Duck2006 on 2006-12-14
This site is worth a look

[http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

---

### Post by dwblas on 2006-12-14
You can put /home on a different partition.  In fact it is a good idea.  If you choose partitions during the install, i.e. do not use auto-partition, you can mount any partition there as /home.  So you will have at least 3 Linux partitions mounted, one as root (/), one as swap (no mount point), and one as home (/home).  If you want, you can wait until after the install and edit /etc/fstab to mount /home for whatever partition you want.  You will also have to mount the new partition at /media/hd??, move the contents of /home to the new partition-just the contents, not /home, unmount the new partition, and remount which should mount it as /home.  After that, it will be mounted at /home every time.

---

