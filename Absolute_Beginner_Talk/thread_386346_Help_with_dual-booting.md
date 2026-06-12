---
title: "Help with dual-booting"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by solinent on 2007-03-16
I am re-installing ubuntu, because of conflicting drivers which confused the heck out of me and made me uninstall things I shouldn't have :(

Anyways, I want to start clean.  Now, I am slightly confused as to the default mount points that ubuntu has set up for me.

Here is what the partitions are:
/dev/sda1
Windows partition -- I plan on mounting this to /media/windows after (fstab).

/dev/sda2
/dev/sda3
- >    /dev/sda5

These are all linux partitions I want to reformat and re-install linux to (sda2 is ext3 for linux filesystem, sda3 I have NO idea whatsover, and sda5 is the linux swap (no idea what that is, but remember it). **edit: I searched and now I know it is used as an extention of memory (virtual memory).  No need to educate me here!**

This is the next screen the installer gives me. (I'm installing by DVD by the way)

Mount point:
1. /dev/sda1
2. swap
3. /

Partition
1. Partition 1 Disc (sda1)
2. Partition 5 Disc (sda5)
3. Partition 2 disc (sda2)

Now I believe that means that it already recognizes windows ntfs (sda1) and is going to mount it to /dev/sda1, then sda5 will be linux swap, and sda2 will be the primary filesystem (/).

Now what will sda3 be used for?  

Am I safe?  It says its going to reformat sda2 and sda5 but not sda1 (which is windows, it shouldn't.)

Can someone tell me what sda3 was installed for, why is there no sda4 and if I press next I won't screw up?  It seems alright to me, but last time I had to manually mount windows myself (ubuntu didn't detect it) and I see no reason for ubuntu to detect it this time (other than ubuntu knowing that its there).


Thanks for taking the time to read that!

---

### Post by K.Mandla on 2007-03-16
If I remember right, there's a partition marker at /dev/sda3 that points to /dev/sda5, which is the swap partition. I believe it jumps from 3 to 5 because the swap is set as a logical partition, and won't infringe on the four-partition limit for primary partitions. 

So in short, yes, you should be safe with that. The Ubuntu partitioner is usually very reliable, and usually won't overwrite something unless you explicitly tell it to do so.

---

