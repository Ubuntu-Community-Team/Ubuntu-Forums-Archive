---
title: "Please help - extreme newbie"
date: 2010-06-11
forum: Apple Hardware Users
---

### Post by Ryan Sweeney on 2010-06-11
Hey guys...

I'm a newbie when it comes to Linux.  I'm having the hardest time partitioning the drives like I need them to be.  Here's the scoop.

I have an Apple Dual G5 Xserve with 8GB of RAM and three 80GB hard drives.

I want to run RAID 5 and run a LAMP server....that's it.

I have a bootable Lucid Lynx disc that is working just fine.  I partitioned the drives according to the documentation I found online, but during the install it said it needed an Apple Bootstrap partition.

Can someone give me some guidance on how to partition these drives with the 10.04 bootable CD, if that's even possible.  

We are mostly Mac here, so this is new to me.  Please don't flame me too badly....I said I was a newbie!  :D

---

### Post by labinnsw on 2010-06-13
You may be new to Linux or Ubuntu but it seems you have a fair understanding of partitioning. Boot up with the live CD and use Gparted (System >> Administration >> Gparted) to make your partitions. Gparted is extremely newbie friendly.:p

I have decided to include [a link I found]("http://www.dedoimedo.com/computers/gparted.html").

---

### Post by shawnhcorey on 2010-06-13
All PowerMacs use Apple's HFS+ as their native file system.  Each bootable drive requires a Apple_Bootstrap partition which typically contains the yaboot boot loader.  The boot partition must be the second partition in the drive's partition map but can be physically located anywhere on the drive.

The best way I know of of creating the boot partition is to use mac-fdisk (available on the CD).  When you start it, use 'p' to print out the map, 'b' to create the boot partition, and 'r' to rearrange the map so the boot partition is the second in the map.  Use 'h' to list a simple help menu.

Best of luck.  :);)

BTW, you should choose a more meaning title like "Need Help with Partitions".

---

### Post by linuxopjemac on 2010-06-14
[http://mac.linux.be/content/apple-powerpc-wiki](http://mac.linux.be/content/apple-powerpc-wiki)

---

### Post by Ryan Sweeney on 2010-06-14
> **labinnsw said:**
> You may be new to Linux or Ubuntu but it seems you have a fair understanding of partitioning. Boot up with the live CD and use Gparted (System >> Administration >> Gparted) to make your partitions. Gparted is extremely newbie friendly.:p

I have decided to include [a link I found]("http://www.dedoimedo.com/computers/gparted.html").

Is there a difference between the install CD and a "Live CD"?  If so, where do I get the "Live CD"?  If not, how do I boot into Linux from the CD without starting the installer?

Sorry if these are basic questions...I'm just so new to all of this Linux stuff.

---

### Post by Ryan Sweeney on 2010-06-14
> **shawnhcorey said:**
> All PowerMacs use Apple's HFS+ as their native file system.  Each bootable drive requires a Apple_Bootstrap partition which typically contains the yaboot boot loader.  The boot partition must be the second partition in the drive's partition map but can be physically located anywhere on the drive.

The best way I know of of creating the boot partition is to use mac-fdisk (available on the CD).  When you start it, use 'p' to print out the map, 'b' to create the boot partition, and 'r' to rearrange the map so the boot partition is the second in the map.  Use 'h' to list a simple help menu.

Best of luck.  :);)

BTW, you should choose a more meaning title like "Need Help with Partitions".

When you say "available on the CD" are you talking about booting up on a Mac OS X CD or the Linux CD?  

Oh, and I'll be sure to be more descriptive in the title next time...Frustration set in the other day when I started this thread.

---

### Post by shawnhcorey on 2010-06-14
> **Ryan Sweeney said:**
> When you say "available on the CD" are you talking about booting up on a Mac OS X CD or the Linux CD?

I don't think it's available on OSX but I haven't ran OSX in years.

If you're running OSX and insert the Linux CD, it should automount and the path would be something like /cdrom/sbin/mac-fdisk (YMMV).  If you boot from the Linux CD, it would be /sbin/mac-fdisk

Documentation for it is [available on-line]("http://www.debian.org/releases/3.0/powerpc/mac-fdisk.txt").

---

