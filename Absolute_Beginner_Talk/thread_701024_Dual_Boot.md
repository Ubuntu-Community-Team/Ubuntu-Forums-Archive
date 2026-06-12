---
title: "Dual Boot"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by layst on 2008-02-18
Hey.
I currently have gutsy installed. but i need to make another partition so that i can install windows. i would like to have the option of booting into either. Can someone please tell me how i can do this. I have an xp cd. and i tried to find a partition app (couldnt find one). Please help i dont like the hassle that windows brings with it but i need it for uni.

---

### Post by jcitguy78 on 2008-02-18
what are your specs for the computer? Have you tried GParted?

---

### Post by mbailey90 on 2008-02-18
put the xp cd in and it should come up for the partitioning the drive.

---

### Post by Hobo Joe on 2008-02-18
Download [this]("http://gparted-livecd.tuxfamily.org/index.php") and burn it as a bootable CD.(The same way you burned the LiveCD).

Once you've booted into it, Find the section with the most free space on your HDD, then resize the partition that it's in. 
From the new empty space you just made, add a new partition, and format it as NTFS.(This step is actually optional, you can do this from either the Gparted CD or the Windows install CD, I'd recommend using the Gparted CD though, I've had bad experiences with the Windows partitioner.)

Then, install Windows how you normally would, but take care to select the right partition so you don't overwrite your Ubuntu install.

Now, this is the tricky part, when Windows installs, it overwrites the boot sector, so you lose Grub. (what you use to choose OS's when you boot your computer.) By overwriting GRUB, Windows makes it impossible to boot into Ubuntu without reinstalling GRUB again.
The easiest way to do that is to get the [Super GRUB Disk.]("http://supergrub.forjamari.linex.org/") Burn it as a bootable disk, as before. Then, boot into it. For the most part, it will walk you through everything, and somewhere there will be an option to re-install grub. Do that, then reboot your computer and you're done!

---

### Post by oedha on 2008-02-18
mmm.....i am just curious......
can we install windows after ubuntu ?

---

### Post by Hobo Joe on 2008-02-18
> **oedha said:**
> mmm.....i am just curious......
can we install windows after ubuntu ?

Yep, it's a pain though because it overwrites the boot sector. See my above post.

---

### Post by jcitguy78 on 2008-02-18
You can but it's easier to do to the other way around. Refer to post before yours it explains it nicely.

---

### Post by oedha on 2008-02-19
mmmm......thanks...maybe i'll give a shot here :)

---

