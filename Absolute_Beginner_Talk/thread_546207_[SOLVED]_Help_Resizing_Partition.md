---
title: "[SOLVED] Help Resizing Partition"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Enishiru on 2007-09-08
I recently installed Ubuntu on my laptop, which was already running Windows.

I made a partition, but it was much bigger than I had wanted, taking up about 50% of my hard drive.

Reading some posts on the forums, I decided to use gparted. I made a live cd and used it to resize my Ubuntu partition to around 8GB.

The problem is, now there is around 30GB of "unallocated" space. I can't seem to make my Windows partition any larger.

Is there any way I can add the 30GB to my Windows partition?

Any help would be appreciated.

Thanks.

---

### Post by jnorthr on 2007-09-08
It depends where the extra space is located. Is it just after the windows partition ? If you've just done a ubuntu install, you might just toast the ubuntu partitions except the windows partition then give all the space back to that partition. Then reinstall ubuntu. The live Cd install does have a quite good version of supergrub which does the same as gparted, you can manually divide up the (hopefully single) partition into the typical ubuntu setup of 1)windows 2) swap partition (about twice size of your ram) and 3) root ( / ) partition. If your windows partition is fat32, then ubuntu can read/write to it like it was it's own ...

---

### Post by bodhi.zazen on 2007-09-08
no, no, no

You need a newer version of gparted.

Use the gparted live CD :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

### Post by Enishiru on 2007-09-08
The Windows partition is set to "ntfs", though I don't know what any of it means.

It's followed by the Ubuntu partition, then the "unallocated space".

I used the live cd from the start. Should I format my Windows partition to something else? Or would be problematic?

---

### Post by diatribe on 2007-09-08
if you just installed ubuntu, it would probably be easier to use gparted to remove your ubuntu partition, then resize your windows partiton, then set up your ubuntu partitions

---

### Post by bodhi.zazen on 2007-09-08
> **Enishiru said:**
> The Windows partition is set to "ntfs", though I don't know what any of it means.

It's followed by the Ubuntu partition, then the "unallocated space".

I used the live cd from the start. Should I format my Windows partition to something else? Or would be problematic?

As I indicated, you need a newer version of gparted.

You need to move the partitions so the free space is adjacent to the ntfs partition, then resize.

---

### Post by Enishiru on 2007-09-08
Well, I just downloaded gparted this morning, so it is the most current version.

I was unable to move the unallocated space, however.

I deleted the ubuntu partition, and was able to give the unallocated space to my Windows partition.

However, upon rebooting, GRUB started and there was an error (error 22 I think).

So now I can't get past the GRUB phase and can't access my Windows OS.

I'm going to try and boot from the Ubuntu Live CD and reinstall it.

Please help if you can.

---

### Post by bodhi.zazen on 2007-09-08
he he he , good idea, but well, not what I would have advised. You can not boot because you deleted the Ubuntu partition. You need to re-install ubuntu or fix the window boot loader.

What to do :

1. set up your partitions with gparted. You need one for / (ubuntu root) and a swap partition (swap = ram x2, max 1 Gb is typical).

2. Re-install Ubuntu. This will fix your problem in a flash.

---

### Post by Enishiru on 2007-09-09
Thanks for all your help.

I created a partition with gparted, but I didn't make a swap partition (this was all before I read your post).

Fortunately, the reinstall of ubuntu worked anyway, and now everything is fine. I could have lost all my data, but instead the repartition worked the way I intended.

I consider myself fairly lucky. Maybe next time I'll read the documentation :)

Again, thanks for your help. I appreciate your time.

---

