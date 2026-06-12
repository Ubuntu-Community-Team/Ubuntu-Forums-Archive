---
title: "Primary partition grayed out on SATA drive"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by tkstock on 2007-02-22
Hello,

I've been playing around with Ubuntu on my son's 800MHz machine, but want to go ahead and install it on my main computer (2.8GHz, 1GB RAM, decent graphics card) so I can see it in action with things like Beryl and try to use it on a more-regular basis.

I want to set this up as a dual boot with Windows XP.  I have 3 HDD's, (160GB SATA, 80GB SATA, 60GB IDE).  The 160GB drive has my primary windows partition (about 60GB) which I don't want to touch.  I created a 15GB partition at the end of the 160GB drive to accomodate Ubuntu.

When I get to the point in the installation where I'm asked to set up my partitioning, I try clicking "Use the largest continuous free space" - this returns me right back to the same place!  If I try to set it up manually, the 15GB space is shown as unallocated, but I can only create logical partitions there - I can't create a primary partition!  When I attempt to divvy up the space (7GB for /root, 7GB for /home, 512MB for swap) I can create the logical partitions successfully, but the next step tells me I don't have a root drive!  What am I doing wrong?

Thanks for your help!

---

### Post by mikewhatever on 2007-02-22
Ubuntu runs very well on my logical partitions (root, swap), so that should not be the problem. About the root problem, This mount point /root should read as simply /, which is root.

---

### Post by tkstock on 2007-02-22
> **mikewhatever said:**
> Ubuntu runs very well on my logical partitions (root, swap), so that should not be the problem. About the root problem, This mount point /root should read as simply /, which is root.

So you don't have to create a primary partition?

Ok, well, I was able to create logical partitions just fine, but when I try to go to the next step, it tells me I don't have root.

The way I set it up:

/ - 7GB ext3
/home - 7GB FAT32
swap - 512MB swap

Do I need to specify a /boot mount point somewhere?

---

### Post by tkstock on 2007-02-22
Nevermind - it appears to be working now... something was acting quirky before.  I guess the installer isn't bug free if you have to go back and re-do some things every now and then.

---

