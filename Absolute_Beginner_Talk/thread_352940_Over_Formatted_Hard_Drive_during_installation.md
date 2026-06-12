---
title: "Over Formatted Hard Drive during installation"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by reswob on 2007-02-04
Hi, I usually do a search before posting, but I seriously doubt anyone else has had this problem.  

I have already had one question answered tonight and then I found this larger problem.

My machine has two hard drives and is a dual-boot between Windows XP and Ubuntu. XP is installed on the primary drive which has two partitions, 31 MB for some Dell junk and 19 GB for XP formatted NTFS. The second drive is where I installed Ubuntu.  It is a 40 GB drive and I had a primary partition of 15 GB that had stuff on it for Windows.  The remaining part of the hard drive was where I wanted to install Ubuntu.  During the install, I (thought I) was very careful to select the remaining part of the drive, have gpart configure it as a ext3 and a swap partition and have Ubuntu install there.  

When I went into XP and it couldn't find certain data I discovered Ubuntu had formatted the ENTIRE disk.

I assume data gone bye bye?  

I don't remember if I missed some warning message or something saying it was going to format 40 GB, but I'm positive that during the install I chose 'Manually edit partition table' and then created two new partitions for ext3 and swap and only those partitions were checked to reformat and the sizes said 17 GB and 1004 MB.  Did I miss something somewhere else?



I

---

### Post by pseudonym on 2007-02-04
Post the output of this command - ```
sudo fdisk -l
```

---

### Post by bodhi.zazen on 2007-02-04
> **reswob said:**
> Hi, I usually do a search before posting, but I seriously doubt anyone else has had this problem.  

I have already had one question answered tonight and then I found this larger problem.

My machine has two hard drives and is a dual-boot between Windows XP and Ubuntu. XP is installed on the primary drive which has two partitions, 31 MB for some Dell junk and 19 GB for XP formatted NTFS. The second drive is where I installed Ubuntu.  It is a 40 GB drive and I had a primary partition of 15 GB that had stuff on it for Windows.  The remaining part of the hard drive was where I wanted to install Ubuntu.  During the install, I (thought I) was very careful to select the remaining part of the drive, have gpart configure it as a ext3 and a swap partition and have Ubuntu install there.  

When I went into XP and it couldn't find certain data I discovered Ubuntu had formatted the ENTIRE disk.

I assume data gone bye bye?

If you formatted and then wrote over the partition, yes, bye bye data, unrecoverable :(

You MAY be able to rescue some of the data, but do not count on it.

First thing is to remove the HD from your computer to keep from continuing to overwrite your potential data.

Then seek professional help ;)

Before we conclude that however ...

Boot to the live (desktop) cd. Open a terminal. Post the output of : ```
sudo fdisk -l
```That's a small "L" not the number 1

Lets see what you have ...

---

### Post by reswob on 2007-02-04
Thanks for the help.  I did sudo fdisk -l and indeed it showed the other partition went bye bye.

Fortunately I did back up all my important data (that is, I hope I got it all).  

That, however, does lead to another question, will Ubuntu have issues if I shrink its partition and create a new one to reload the applications that got deleted?

---

### Post by annda on 2007-02-04
go ahead. i did it 2 days ago with a gparted livecd and it took some 10 minutes on a 160GB disk. no data lost, everything works fine.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

