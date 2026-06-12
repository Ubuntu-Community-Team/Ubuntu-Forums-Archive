---
title: "Installing Ubuntu- Partioning"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Seldoms on 2006-08-17
I want to choose the first option to do it automatically. However, will this give all the free space to ubuntu? I want to do it automatically but I also want to have space left on the windows partition.

---

### Post by bodhi.zazen on 2006-08-17
Since no one else has responded I will.

You need to partition prior to install.

First defrag your windows partition. Then resize.

You now will have free space on the hard drive. You can, I believe, auto partition this free space during the Ubuntu install. Ubuntu will use all of this space.

---

### Post by ComplexNumber on 2006-08-17
**Seldons**
when you are partitioning ubuntu, have a root partition, a home partition, and a swap partition.

---

### Post by Seldoms on 2006-08-17
I already defragged windows. How do I resize?

I want to leave some space for windows. I would game on windows but surf and use ubuntu otherwise. I think 5gb would get good for that on Ubuntu. How do I set that up?

---

### Post by bodhi.zazen on 2006-08-17
If you run the ubuntu "live" cd run GParted.

Search the Ubuntu forums as there are multiple treads with instuctions re: partitioning.

5 GB is sufficient for Ubuntu if you do not plan to install much software. You will also need a swap partition, typical size is RAM X 2.

---

### Post by az on 2006-08-18
> **bodhi.zazen said:**
> 
You need to partition prior to install.


No.

The ubuntu installer can do it for you.

You want to have free space left on your windows drive?  Just make the partition bigger than the space that is filled.  

You tell the installer what size to shrink the windows partition down to.  It's actually the only partitioning question you get asked when you do it the automagic way.

And you do not need a home partition.  The default is one partition for your filesystem and one for swap (virtual memory on disk).

The installer does all that for you.

---

### Post by Seldoms on 2006-08-18
I thought 5gb would be enough too. But would it be enough to download the 'cool' applications?

---

### Post by az on 2006-08-18
> **Seldoms said:**
> I thought 5gb would be enough too. But would it be enough to download the 'cool' applications?

About 2 gigs of disk space is used by the desktop installation and swap.

---

### Post by Seldoms on 2006-08-18
Hmm, so maybe do 8 gigs?

---

### Post by bodhi.zazen on 2006-08-18
azz:

Thank you for the information, but I am not sure what you are referring to. Are you referring to the live CD or the alternate CD?

I am not as familiar with the live CD. I thought the Live CD used GParted. Are you saying GParted is launched during the install from the live CD? I have always assumed you run GParted then the installer.

With the alternate CD I am aware of cfdisk, but cfdisk does not re-size a partition. Later you can format a partition, or create a partition in free space, but again not re-size a partition.

---

### Post by az on 2006-08-20
> **bodhi.zazen said:**
> azz:

Thank you for the information, but I am not sure what you are referring to. Are you referring to the live CD or the alternate CD?

Both.

> **bodhi.zazen said:**
> 
I am not as familiar with the live CD. I thought the Live CD used GParted. Are you saying GParted is launched during the install from the live CD? I have always assumed you run GParted then the installer.

No.  The installer will offer to automatically resize a windows partition for you to free up some free space.  However, 
1.  The partition table has to be intact (sometimes you can be running windows with a borked partition table)
2.  The windows partition has to have enough free space left on it.

If one of the two of the above is true, then you only get offered two options - erase entire disk and manually partition.  The manual partitioning step launches Gparted.

> **bodhi.zazen said:**
> 
With the alternate CD I am aware of cfdisk, but cfdisk does not re-size a partition. Later you can format a partition, or create a partition in free space, but again not re-size a partition.

It is the same as the live cd, with the automatic partitioning step offered.  The manual partitioning step lauches a curses frontend to parted.  It is more-or-less the same as Gparted, but in curses (text).


You haven't needed cfdisk since Debian Woody.  Warty released with a decent partitioner, but ntfstools was not mature enough for release and so you could not resize ntfs.  That was fixed in Hoary.

---

### Post by bodhi.zazen on 2006-08-20
Thanks azz. I guess it has been a while since I have partitioned with the Ubuntu install disk.

---

