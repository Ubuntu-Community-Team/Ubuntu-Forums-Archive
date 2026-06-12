---
title: "what is the swap partition and missing HD space"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-05-09
What is the swap partition in linux? Is there something interesting one could do there?

Also I notice through mt disk manager that my mounted hd is the approx. 170Gb but my HD is 200GB. Where is that other 30Gb? This is what I get back from fdisk -l:

root@NARUTO:/home/cristian/Desktop/pidgin-2.0.0# fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23970   192538993+  83  Linux
/dev/hda2           23971       24321     2819407+   5  Extended
/dev/hda5           23971       24321     2819376   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9728    78140128+   7  HPFS/NTFS
root@NARUTO:/home/cristian/Desktop/pidgin-2.0.0# 

Everything seems to be there... like all the hard drive? maybe the HD space missing is in that extended partition? If so.. to get access to it... should I mount it? How can I do that? Thxs... Cristian

---

### Post by starcraft.man on 2007-05-09
Swap partition also called the swap-file, is well the same as  a paging file in windows if you know what that is. Basically it is simply a buffer of space on your HDD for the computer to use when/if it runs out of hardware ram. It is of course very bad for a computer to ever run out of ram space, of course the small problem is that if your system is forced to use swap file for something intensive it will of course be slower than dedicated ram. Even if you have lots of ram, Ubuntu still needs swap space because some things expect it to be there and naturally use it rather than bogging down the ram.

I'm not really sure whats with your hard drive >.>

/dev/hda1 * 1 23970 192538993+ 83 Linux

Just me doing my math but thats.... 23.97 MB and 192.54 GB, giving your linux partition 192.30 GB. Seems like your whole hard drive is there. The 6 (2 are your swap) GBs are lost because the box puts the decimal number of GB, where as the partition shows the binary number. Are you sure you lost 30?

EDIT: Just a note but thats a HUGE partiion for Linux. Why didn't ya make a home partition and put your data there? One giant root directory will lead to problems if you ever have to reinstall or upgrade (and it fails). You may want to consider putting 180 GB in a /home partition and keeping 10 for Ubuntu.

---

### Post by csf111 on 2007-05-09
Your swap partition is a kind of "cache"
This is a reserved area of your hard drive 
that Ubuntu will use if your applications 
require more ram (memory) then you have
in your system.

You don't mount it, it's for the SYSTEM

---

### Post by krisfrajer on 2007-05-09
thxs guys... yeah swap=cache.. makes sense now. 

About the HD space missing... my bad I misinterpreted the information given by Linux desktop. I did the math too and all the space is there. Thxs anyways!

---

### Post by deanjm1963 on 2007-05-09
is your hd 200gb formatted or 200gb unformatted? I have a 160gb hd but it formats to about 149gb

also, depending on which file system you used the amount available can vary. ext3 on general keeps 5% of space for itself, mainly for "root" usage, it goes back to the olden days when hard drives were only a couple of gb so root would have enough room for updates, etc.

---

### Post by starcraft.man on 2007-05-09
> **krisfrajer said:**
> thxs guys... yeah swap=cache.. makes sense now. 

About the HD space missing... my bad I misinterpreted the information given by Linux desktop. I did the math too and all the space is there. Thxs anyways!

No problem, we are always here to help. Glad to clear things up. Do think about the home partition thing, you will find it helpful if you ever need to do something to your root directory without losing your data.

---

### Post by krisfrajer on 2007-05-09
Can I repartition my disk right now as it is or should I go and repartition and reinstall all ubuntu again?
I think it is smart to break down this huge monster...

Yeah I also notice that my hard drive is 200Gb but in the system ends up being about 190Gb... I am ok with those other Gb's not been displayed... I am sure Ubuntu is making good usage of it. C.

---

### Post by starcraft.man on 2007-05-09
> **krisfrajer said:**
> Can I repartition my disk right now as it is or should I go and repartition and reinstall all ubuntu again?
I think it is smart to break down this huge monster...

Yeah I also notice that my hard drive is 200Gb but in the system ends up being about 190Gb... I am ok with those other Gb's not been displayed... I am sure Ubuntu is making good usage of it. C.

You can actually use the partitioner to resize your main partition down to 10 GB. I don't really recommend it though, there is always the chance that errors are made when resizing the parition. Especially in your case, since you haven't done anything just reinstall since you don't seem to mind the other 6 times :p

Manually partition this set up, at least its my recommendation for ya. I won't give you step by step instructions cuz the partitioner is very straight forward (you just select free space and enter to create a partition for instance :) ):

Mount point : **/**
Format: Ext3
Type: Primary
Size: 8 GB

Mount point : /home
Format: Ext3
Type: Logical
Size: X (remainder of your drive - (8 GB + 2 GB swap)

Mount point: swap-file (doesn't actually mount, just for consistent list :))
Format : swap-file
Type: logical
Size: 2 GB

That should be it, the above is my generic install, it works for almost everyone :) Have fun with Ubuntu after you get it finally installed, and read ubuntuguide in my sig to learn more :)

---

