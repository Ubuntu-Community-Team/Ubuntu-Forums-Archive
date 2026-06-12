---
title: "[SOLVED] Installing ubuntu and need to know the best way to partition out my hard dri"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by travismoore on 2008-01-14
I have an 80GB and a 500GB HDD. I am intending to use the 80GB for the OS's and the 500GB for storage. (I am dual-booting)

My 80GB is NTFS and has a fresh windows install on it. I am going to allocate 38GB of it for ubuntu and 2GB for the swap. The remaining 40GB will be windows.

I want to put my /home on the 500GB and what ever windows stuff i need on the there as well.

I need to know how to partition out the 500GB(currently NTFS) so that i can use it for linux and windows and transfer files between the two.


thanks,

Travis

---

### Post by Jeremiah_P on 2008-01-14
bump... I was actually considering the same setup and would be interested in reading an experienced user's recommendation on doing this.  Aren't you supposed to install Windows first, though?

---

### Post by polmir on 2008-01-14
You will need to visit:

[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

I hope this helps.

---

### Post by travismoore on 2008-01-14
> **Jeremiah_P said:**
> bump... I was actually considering the same setup and would be interested in reading an experienced user's recommendation on doing this.  Aren't you supposed to install Windows first, though?

I said i have a fresh install of windows on the 80GB

---

### Post by Hightide on 2008-01-14
I would recommend the use of GParted live CD as indicated above. Download onto CD, reboot to CD and follow instructions.

its not difficult
:)

---

### Post by travismoore on 2008-01-14
Cheers,

But want a need to know is what i should do with the 500GB, NTFS? FAT32?        Ext3 and NTFS?

I need to have windows files and ubuntu files on both and i need to transfer them between each other.

---

### Post by vikram on 2008-01-14
Its great that you have a dedicated /home partition

you have two choices for the 500G disk.
you can make it NTFS and use ntfs-3g driver to use linux to also rw. I haven't used this option

2 you can format the 500G as ext3 and use the windows ext2 driver for reading and writing in windows. Have used it for a couple of years without incident though I rarely boot windows any more.

---

### Post by bodhi.zazen on 2008-01-14
1. Backup any data first.

2. Defragment your windows partition.

3. Gparted is on the Ubuntu desktop CD, so no need to download / burn the gparted live CE, although it is a nice tool.

4. You are unlikely to need a swap larger then 1 Gb. The exception would be if you are running a laptop and want to suspend. It sounds like you have a desktop, and thus 1 Gb swap is fine.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by bodhi.zazen on 2008-01-14
> **vikram said:**
> Its great that you have a dedicated /home partition

you have two choices for the 500G disk.
you can make it NTFS and use ntfs-3g driver to use linux to also rw. I haven't used this option

2 you can format the 500G as ext3 and use the windows ext2 driver for reading and writing in windows. Have used it for a couple of years without incident though I rarely boot windows any more.

You can not as of yet install Linux on a NFTS file system, even with the use of ntfs-3g

---

### Post by Vadi on 2008-01-14
The Ubuntu liveCD has gparted already though, why would you get another cd for it?

---

### Post by Terry of Astoria on 2008-01-14
I suggest making your home partition ext3. It is much more secure and robust. One thing is file ownership and permissions are more advanced on ext3 so your files are more secure and also no need to defrag.
Windows can access it using the special driver.
You may want to make a (perhaps smaller) NTFS partition just in case. Of course, FAT32 would be accessible from Win98 too but NTFS is a more robust files system.

---

### Post by travismoore on 2008-01-14
Cheers for  the help guys,

so it looks like i make the 500GB Ext3 ? 

could i not do the 500GB half NTFS half Ext3 and adjust it later?

Oh yea i use XP if thats any use.

---

### Post by Terry of Astoria on 2008-01-14
I think if I were you I'd make it like 420 GB ext3 and 80 GB NTFS - the NTFS part just in case you need to move files there for access from Win without the ext3 driver.

---

### Post by Terry of Astoria on 2008-01-14
Put the NTFS partition last on the drive - Then it's safer later to remove it and "grow" your ext3 partition to fill the freed space.

---

### Post by travismoore on 2008-01-14
thanks, just one last thing

I have some files backed up on the 500GB currently so I don't want to go formatting it because i will loose stuff. So can i put ext3 first on drive without loosing the stuff I  have on the NTFS already?

---

### Post by vikram on 2008-01-15
> **bodhi.zazen said:**
> You can not as of yet install Linux on a NFTS file system, even with the use of ntfs-3g

A quick read of the ntfs-3g faq tells me that the driver can be used to mount not just the /home but also the root as used in WUBI

the source of this info

[http://www.ntfs-3g.org/support.html#rootfs](http://www.ntfs-3g.org/support.html#rootfs)

That said i havent tried it yet. also I will also always recommend an open FS like ext3 to ntfs all other things being equal .

---

### Post by bodhi.zazen on 2008-01-15
> **vikram said:**
> A quick read of the ntfs-3g faq tells me that the driver can be used to mount not just the /home but also the root as used in WUBI

the source of this info

[http://www.ntfs-3g.org/support.html#rootfs](http://www.ntfs-3g.org/support.html#rootfs)

That said i havent tried it yet. also I will also always recommend an open FS like ext3 to ntfs all other things being equal .

That is not the same thing. WUBI is installed into a file that is formatted to ext3 (siminar to installing Ubuntu in a virtual machine). The file system used by Ubuntu / Linux is NOT ntfs (although the file or virtual disk is stored on a ntfs file system).

See here :

[http://sourceforge.net/potm/potm-2006-09.php](http://sourceforge.net/potm/potm-2006-09.php)

> What's on your project wish list?

Anton: Full read-write support; we are working on it. My personal wish list also includes an NTFS filesystem checker (a Windows chkdsk replacement) so people do not have to boot Windows to check/repair their NTFS volumes.

Yuval: Allowing Linux to use NTFS as the root/boot partition.

Yura: Ability to install Linux on an NTFS volume.
So as of yet a ntfs filesystem (partition) can not be mounted as / or /boot.

---

### Post by szaka on 2008-01-15
> **bodhi.zazen said:**
> So as of yet a ntfs filesystem (partition) can not be mounted as / or /boot.
Technically speaking, they can be. I tried it myself too in 2006 using Gentoo (since I didn't really believe such user reports). The only needed trick was the use of the 'dev' mount option because FUSE defaults to nodev so file operations involving /dev/null failed. However the system is basically runs in single user mode. 

Last year full file permission and ownership support was also implemented which was a huge step towards full feature NTFS root. The main missing part is the dynamic Windows-Linux user mapping. Currently static user mapping is a prerequisite.

---

### Post by bodhi.zazen on 2008-01-15
Thanks for the info.

Since this is "Absolute Beginners Talk" I think we should be clear for new users.

While what szaka is proposing may be technically possible, I would not say it is "main stream". I am not sure using ntfs for /boot or / is good advice to new uses at this time. I advise new users stay with LInux native file systems (ext3, reiserfs, XFS, etc).

---

### Post by barney385 on 2008-01-15
Have you considered doing a Raid 0?

---

### Post by travismoore on 2008-01-15
whats that?

---

### Post by barney385 on 2008-01-15
A Raid 0 array would make your two hard drives one large virtual hard drive.
 
There is lots of info out there and how-to's.
 
Just an idea you might want to investigate before proceeding.
 
Then again, maybe not.
 
Good luck with whatever avenue you decide on.
 
:guitar:

---

