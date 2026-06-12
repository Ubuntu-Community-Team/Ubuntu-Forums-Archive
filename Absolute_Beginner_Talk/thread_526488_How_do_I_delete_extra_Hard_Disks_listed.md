---
title: "How do I delete extra Hard Disks listed"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by gibsongirl on 2007-08-15
I have an Emachines e-tower 366c:
cpu: Cyrix MII-366 (w/ 512KB l2 cache) Processor
Mem: 32 syncDram (up to 256 MB)
HD: 3.2GB HDD (Ultra Dma Eide)

When I open the disk menu, I find three hard disks listed.

#1 Samsung SV0322A
2.98 GiB
/dev/hdc

#2 Unionfs

#3 Tmpfs

I want to know how I can get rid of the other two.  They are causing a problem for me. Thanks for your help.

Gibsongirl

---

### Post by Hobo Joe on 2007-08-15
Paste the ouput of 
```

fdisk -l

```

They may not be separate drives or partitions, this is just to check.

---

### Post by Steve1961 on 2007-08-15
2 and 3 are not disks, they're file systems.  From wikipaedia:

> UnionFS is mainly used in Live-CD or diskless systems, where the read-only root directory is combined with a tmpfs filesystem (which resides in memory and is writable). This way, all the files from read-only root can be modified, and the modification is kept in memory.

---

### Post by Inxsible on 2007-08-15
> **gibsongirl said:**
> I have an Emachines e-tower 366c:
cpu: Cyrix MII-366 (w/ 512KB l2 cache) Processor
Mem: 32 syncDram (up to 256 MB)
HD: 3.2GB HDD (Ultra Dma Eide)

When I open the disk menu, I find three hard disks listed.

#1 Samsung SV0322A
2.98 GiB
/dev/hdc

#2 Unionfs

#3 Tmpfs

I want to know how I can get rid of the other two.  They are causing a problem for me. Thanks for your help.

Gibsongirl
You have only 32 MB memory ? What flavor of Linux are you running on it?
Also with only 3.2 GB HDD, it would be very difficult to do anything on it :(

---

### Post by Hobo Joe on 2007-08-15
> **Inxsible said:**
> You have only 32 MB memory ? What flavor of Linux are you running on it?
Also with only 3.2 GB HDD, it would be very difficult to do anything on it :(

Just to double check with someone who knows what they are talking about, 'fdisk -l' is the right command to check the disk, right? :-?

---

### Post by Inxsible on 2007-08-15
> **Hobo Joe said:**
> Just to double check with someone who knows what they are talking about, 'fdisk -l' is the right command to check the disk, right? :-?
Yes, but you should mention that -l is lowercase L, because it looks a lot like 1 (One) in the font for the code :)

Also ```
sudo fdisk -l
``` is a better option coz it will list the internal drives too. Without sudo, it only lists the external drives.

---

### Post by Hobo Joe on 2007-08-15
> **Inxsible said:**
> Yes, but you should mention that -l is lowercase L, because it looks a lot like 1 (One) in the font for the code :)
Woohoo, I was right! 
I was going to, but I just assume that people with cut and paste, but that's probably a bad thing to assume....

---

### Post by gibsongirl on 2007-08-15
For quite a while I ran Ubuntu 6.06 on it then I was able to run 7.04.  However as you can imagine the page loads took forever.  Someone suggested Puppy or Damn Small and I have tried them. I really liked Dsl however I cannot get on the forum page to ask any questions at all.  So I switched back to Ubuntu.

---

### Post by gibsongirl on 2007-08-15
fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/hdc: 3200 MB, 3200311296 bytes
255 heads, 63 sectors/trac, 389 cylinders
Units = cylinders of 16065 * 51= 8225280 bytes

Device Boot         Start                  End             Blocks             Id        System
/dev/hdc1                1                        38          305203+            5           Extended

---

### Post by talby on 2007-08-16
If you liked DSL then you may prefer a minimal install w/ fluxbox window manager.  Check out ["Installation/LowMemorySystems"@help.ubuntu.com]("https://help.ubuntu.com/community/Installation/LowMemorySystems") for more details (scroll down to the fluxbox section).

The DSL apps are listed here ["Featured Desktop applications used in Damn Small Linux"@damnsmalllinux.org]("http://damnsmalllinux.org/applications.html") they use some really lightweight apps.

Another idea maybe to do a xubuntu install then "sudo apt-get install fluxbox" and make that the default, I have done that on a 333 laptop with good results.

cheers

---

### Post by shaydee on 2007-08-16
Hmmmm. I don't quite understand the initial question by gibsongirl. What kind of problem do those two "disks" (which obviously don't seem to be physical devices) cause you ?.

---

