---
title: "Partitions"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by vacguy on 2007-06-08
I am making the switch from Windows XP.  I have 120 gigabytes on one drive and 250 gigabytes on my other drive.  I have about 180 gigabytes that I need to get onto Ubuntu.  On my 120 gigabyte drive I think I should have 1000 megabytes for the swap partition, 4000 megabytes for the root partition and the rest of the 120 gigabytes for my home partition.  What should I do with the 250 gigabytes on the other hard disk?  Should this be a usr partition or what?  I will have a lot of valuable data on this 250 gigabyte drive.

---

### Post by ronocdh on 2007-06-08
> **vacguy said:**
> I am making the switch from Windows XP.  I have 120 gigabytes on one drive and 250 gigabytes on my other drive.  I have about 180 gigabytes that I need to get onto Ubuntu.  On my 120 gigabyte drive I think I should have 1000 megabytes for the swap partition, 4000 megabytes for the root partition and the rest of the 120 gigabytes for my home partition.  What should I do with the 250 gigabytes on the other hard disk?  Should this be a usr partition or what?  I will have a lot of valuable data on this 250 gigabyte drive.
First, before moving anything around or creating partitions, back up all your valuable data on an external hard drive and then unplug it and place it in your closet under a blanket, so your stuff stays safe. The next issue is how much stuff you need inside Ubuntu. You seem to be interested in triple booting rather than erasing WinXP completely, right? In my experience, it's best to keep often-accessed media on one drive/partition and just share it to all the others. Your options are:
[LIST=1]
[*]If you want to save it on the Windows partition, it can be NTFS, but you will only have read capability (no write). 
[*]If your WinXP installation is FAT32, then you'll have both read and write.
[*]If you want to save your media on your Ubuntu partition, you can have read/write in Ubuntu and also read/write in WinXP through the use of something like [this]("http://www.fs-driver.org/"), an installable filesystem for ext2.
[/LIST]

---

### Post by original_jamingrit on 2007-06-08
Don't forget that 1024 MB = 1 GB!!!!

That's an easy mistake to make.  If you set your partitions by thousands of megabytes, you will have left over space.

---

### Post by original_jamingrit on 2007-06-08
Sorry for the double post.

What I did on my machine was set up three partitions, Windows (NTFS), Ubuntu (ext3), plus a swap, and then a FAT32 partition.  Ubuntu Fiesty can read and write to your NTFS partition, but you may need to install some extra stuff to access the ext3 partition from Windows.  That's why I'd include a FAT32 partition, because then both systems would have easy access to your stored information.

---

### Post by hyper_ch on 2007-06-08
4GB for root is too little... make it at least 10Gb

---

### Post by vacguy on 2007-06-08
Thank you for the advice.

---

### Post by ccfjeff on 2007-06-08
> **ronocdh said:**
> ... In my experience, it's best to keep often-accessed media on one drive/partition and just share it to all the others. Your options are:[LIST=1]
[*]If you want to save it on the Windows partition, it can be NTFS, but you will only have read capability (no write).
[*]If your WinXP installation is FAT32, then you'll have both read and write.
[*]If you want to save your media on your Ubuntu partition, you can have read/write in Ubuntu and also read/write in WinXP through the use of something like [this]("http://www.fs-driver.org/"), an installable filesystem for ext2.[/LIST]I don't know if it is supported in Feisty Fawn yet, or if not if it can be imported, but it sounds like read AND write capability to NTFS partitions is available on Linux systems:

     [SIZE=4]**[COLOR=DarkRed]NTFS-3G Read/Write Driver[/COLOR]**[/SIZE]

     [SIZE=-1][COLOR=DarkRed]Updated: June 8, 2007[/COLOR][/SIZE]     [COLOR=DarkRed]*Over a million hits since the stable driver release*[/COLOR] 
[COLOR=DarkRed]
[www.ntfs-3g.org/index.html]("http://www.ntfs-3g.org/index.html")

The NTFS-3G driver is an open source, freely available read/write NTFS driver for Linux, FreeBSD, OS X, and NetBSD. It provides safe and fast handling of the Windows XP, Windows Server 2003, Windows 2000 and Windows Vista file systems. Most POSIX file system operations are supported, with the exception of full file ownership and access right support.

...

     The driver is in **STABLE** status. Please see our test methods and testimonials on the [driver quality]("http://www.ntfs-3g.org/quality.html") page.[/COLOR] 

I am definitely interested in this topic as I am contemplating how to set up partitions on a "new" computer I just purchased.  I too would like to dual boot.  BTW, was "triple boot a typo?

---

### Post by ccfjeff on 2007-06-08
Someone told me that the NTFS file system is more secure or can be made more secure than the Fat 32 system.  How do those compare to the Linux Ext2/3 systems?

Does encryption mess up any of these partition sharing setups?  ie.  Could Windows still access files on a Linux Ext3 partition via [the IFS software for Windows]("http://www.fs-driver.org/index.html") even if it was encrypted?  Conversely, could Ubuntu access encrypted Windows NTFS or Fat32 partitions?  Read and write?

---

### Post by pneaveill on 2007-06-08
NTFS is and has been very buggy and only slightly more secure than Fat32.  Despite exceptions, Linux systems, are, typically far more secure and stable than window$ ever dreamed of being.

---

### Post by ccfjeff on 2007-06-09
nm

---

### Post by vacguy on 2007-06-09
How do I mount my usb hard disk?  I am sure it is ntfs.  It was just showing up but now I can not see it.

---

### Post by vacguy on 2007-06-09
Here is what I am getting.


caleb@vortex:~$ sudo mount /dev/sda
Password:
mount: can't find /dev/sda in /etc/fstab or /etc/mtab
caleb@vortex:~$

---

### Post by ccfjeff on 2007-06-09
> **vacguy said:**
> Here is what I am getting.


caleb@vortex:~$ sudo mount /dev/sda
Password:
mount: can't find /dev/sda in /etc/fstab or /etc/mtab
caleb@vortex:~$

I'm out of my league here, but it does seem like I read somewhere on these forums that you might have to list the partition as well?  

ie.:   caleb@vortex:~$ sudo mount /dev/sda1

Another thought.  Is that a Sata drive?  If not I think you might have to use an "h" instead of an "s" for the disk descriptor:

ie.:   caleb@vortex:~$ sudo mount /dev/hda1

or?

ie.:   caleb@vortex:~$ sudo mount /dev/hda

---

### Post by vacguy on 2007-06-09
What is fstab and mtab?  I think I need to understand more about these.

---

