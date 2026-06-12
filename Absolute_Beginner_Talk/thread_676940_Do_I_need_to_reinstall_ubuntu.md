---
title: "Do I need to reinstall ubuntu?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Prince_Andrei on 2008-01-24
Running Ubuntu 7.10 64 bit w/ 2gb ram, Intel q6600 and 8600gt. My cpu fan recently got misaligned causing the CPU to overheat and shut itself down during boot. It happened many times and I'm worried that the OS is permanently messed up from crashing during boot 30+ times.

My install was working pretty well before. Now I get this type of error fairly regularly. It completely locks up my system so that I have to do a hard reboot. The keyboard and mouse stop functioning, so no combination of keys can do anything.

swap_dup: bad swap file entry
VM: killing process (random app... sometimes Xorg)

I have run e2fsck over the entire boot drive. I have run memtest86+ on my ram. Both appear fine. However, the crashes remain. I've only been using linux for a couple months, so I can't think of anything else I can do. Do I need to format the drive and reinstall? I have a second drive where I keep all my personal files (but not /home), so it wouldn't be the end of the world, although it would be time consuming.

---

### Post by macogw on 2008-01-24
Swap is just where pagefiles go.  Try reformatting your swap partition (reformat it as swap still), and see if that fixes it.  Some temp files might've corrupted in there.

---

### Post by LowSky on 2008-01-24
you could have a failing hard drive, but you most likely messed up some files from the constant lockups

i would reinstall, just make sure your hard drive is ok

---

### Post by Prince_Andrei on 2008-01-24
> **macogw said:**
> Swap is just where pagefiles go.  Try reformatting your swap partition (reformat it as swap still), and see if that fixes it.  Some temp files might've corrupted in there.

Sounds good. How do I reformat it as swap? And how do I recognize what it is? I'm a total beginner. Thanks!

---

### Post by LowSky on 2008-01-24
use Gparted  or ubuntu's LiveCD. You cant do it logged into a regular session of ubuntu.

In ubuntu live cd  menu its under System>Admin> Disk Management or something or other (i at work on a windows machine...blah)

---

### Post by Prince_Andrei on 2008-01-24
> **LowSky said:**
> use Gparted  or ubuntu's LiveCD. You cant do it logged into a regular session of ubuntu.

In ubuntu live cd  menu its under System>Admin> Disk Management or something or other (i at work on a windows machine...blah)

Thank you very much! I'll try that and report back.

---

### Post by Prince_Andrei on 2008-01-24
I reformatted the swap partition but sadly I am still getting an error:

swap_free: bad swap file entry

It caused a fatal X error, and luckily gdm restarted and I didn't have to press restart. I checked my drive for bad clusters and found none. I'm not sure what else to do other than reinstall. Any final ideas?

---

### Post by seventhc on 2008-01-24
when I use gparted from the live cd I usually open a terminal and enter
```
sudo gparted
```
it won't ask you for a password, then once gparted opens you right click on the swap partition and choose swapoff, I'd then delete and recreate it formatting as swap of course. ;)

---

### Post by Prince_Andrei on 2008-01-24
Deleted the swap partition and created a new one. Still get the same crashes. The error message was slightly different (although I haven't always gotten an error message):

gdm[6257]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

It's possible that it is the same problem other 64 bit nvidia users are having.

---

### Post by Prince_Andrei on 2008-01-25
After installing the latest nvidia drivers via Envy I believe my system is now more stable. However, I recently had a kernel panic while booting, so something fundamental may still be messed up.

---

### Post by stoodleysnow on 2008-01-25
We are all assuming you now have a new HSF, right?
:lolflag:

---

