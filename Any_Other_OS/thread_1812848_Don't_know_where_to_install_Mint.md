---
title: "Don't know where to install Mint"
date: 2011-07-26
forum: Any Other OS
---

### Post by BKbroila on 2011-07-26
So currently, I'm dual booting Win7 and Xubuntu. I originally had Win7 and Ubuntu, but that has now changed to what it is now.

I was trying to install Mint Debian XFCE, but got confused as to where I was supposed to install it because I have 3 linux-swap partitions and another for /home. 

Do I install Linux Mint's /root to one of the swap partitions??? Because since the other 2 swap are still existing, would they still try to operate Mint? 

Or should I delete two of those swap partitions, install /root to one of the swap partitions, and then /home over the partition with Xubuntu?

Clarification: I'm trying to get rid of Xubuntu, and get Mint instead, with Win7 untouched in this process
Thanks

---

### Post by benerivo on 2011-07-27
You only need one swap partition, as it can be shared between linux installations on the same computer.

If you want rid of xubuntu you are okay to just keep one swap partition and use the remaining disk space for linuxmint xfce-de. This can all be done as part of the installation process, where you can specify which partition you want mint to use for swap, and which partition you want for root. You can keep a separate /home if you want and have something like...

/dev/sda1 - Windows
/dev/sda2 - swap
/dev/sda3 - / (linuxmint)
/dev/sda4 - /home

---

### Post by BKbroila on 2011-07-27
Would it be possible to combine 2 of my 3 swap partitions? Could I combine 2 of them using GParted while I'm in Xubuntu, or will that mess things up? What about combining those 2 swap partitions with unallocated space that's never been touched?

---

### Post by drawkcab on 2011-07-28
> **BKbroila said:**
> ...because I have 3 linux-swap partitions...

I didn't even know you could do that!

---

### Post by BKbroila on 2011-07-28
Hahaha I don't know why I made 3. I remember when I was asking for help in the beginning before I installed Ubuntu, that people said to make 3 partitions, and I guess I mistakenly made 3 swap....

---

### Post by el_koraco on 2011-07-28
> **BKbroila said:**
> Would it be possible to combine 2 of my 3 swap partitions? Could I combine 2 of them using GParted while I'm in Xubuntu, or will that mess things up? What about combining those 2 swap partitions with unallocated space that's never been touched?

Yes, use the "swapoff" option in the right click menu before you do anything to them. But seriously, if I were you, I'd delete them, make a single ext 4 partition out of them, and install Mint in it. 

I'm supposing Mint XFCE uses the Debian graphical installer. It's a little bit dirrefent than Ubuntu's, but you'll get the hang of it.

---

### Post by BKbroila on 2011-07-28
Alright, I was trying your method, but didn't get any option to unmount any of my partitions. The picture I included is of everything I have on my HDD.
The Storage partition is for all of my media I've shared between Win7 and Linux distros. And /dev/sda1 and /dev/sda2 are both for Win7.

/dev/sda/8 used to be a swap partition, but I changed it to ext4. I tried deleting it, but I get a prompt to unmount it first. And when I right click on the partition, I get no option to unmount it. So I can't delete any of the partitions in  the /dev/sda4 partition.

How do I go about unmounting the partitions?

---

### Post by el_koraco on 2011-07-29
Right click on /dev/sda7, choose "swapoff" and then delete it.

---

