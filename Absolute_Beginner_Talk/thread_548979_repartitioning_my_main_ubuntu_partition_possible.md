---
title: "repartitioning my main ubuntu partition possible?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by informer on 2007-09-12
I've been running Ubuntu for a week now and spent 2 whole days fixing it to work with my notebook (ATI graphics and wireless).  It is a rewarding experience to finally get something to work but now I'm stuck.

I only gave Ubuntu 4GB of space but realised that I'm quickly running out of available space.  

So now I'm trying to give it more space using the live CD GPARTED, but to no avail.

Here are some information :

/dev/sda1 - (FS) ext3 - (mountpoint) /media/disk - (size) 3.72GiB - (used) 3.19GiB - (unused) 541.84MiB
unallocated  - (FS) unallocated - (mountpoint) none - (size) 6.81GiB - (used) none  - (unused) none
/dev/sda3 - (FS) linux-swap - (mountpoint) none - (size) 1.19GiB - (used) none - (unused) none
/dev/sda4 - (FS) fat32 - (mountpoint) /media/disk-1 - (size) 7.81GiB - (used) 3.15GiB - (unused) 4.66GiB
/dev/sda2 - (FS) ntfs - (mountpoint) /media/New Volume - (size) 73.62GiB - (used) 56.72GiB - (unused) 16.90GiB

My main Linux partitions is sda1, trying to add space from the unallocated partition.

The error message I get is :

"The following operation could not be applied to disk :

Resize /dev/sda1 from 3.72GiB to 9.48GiB

Can anyone help?

---

### Post by Shazaam on 2007-09-12
What you could do is make the unpartitioned space your /home partition. Check this page for instructions...
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by hyper_ch on 2007-09-12
Or download the GParted Live CD and do the partitioning from in there....

when you boot up, then your root partition is in use and you can't resize it... that's why you need to boot from something else ;)

---

### Post by humti-dum-ti on 2007-09-12
I do have a similar problem rapartitioning my root partition.
I have sda1 as swap, sda2 as 'free' (intended to purely store data on) and sda3 as the root partition, from where i boot.
Now I want to delete sda2 and give all the free space to sda3.
When I boot from a live cd (ubuntu live cd) and run gparted I can delete sda2 but cannot give that space to sda3. 
Is there a way to fix this problem?

Thx, humti

---

