---
title: "More help partitioning--home partition won't exceed 50GB"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by hul on 2007-06-25
Hello!  I'm trying to partition a 500GB hard drive, 2GB RAM.  I haven't done this before and am running into issues.

I'm installing Ubuntu FF 7.04 off of the live CD.  I want to set up the partitioning this way:
Device - Type - Mount point - Format? - Size
/dev/sda3 - ext3 - /home - yes - 475100 MB (Primary)
/dev/sda2 - ext3 - / - yes - 20003 MB (Primary)
/dev/sda1 - swap - N/A - N/A - 5000 MB (Primary)

I created the swap partition first, then the "/" partition, and I'm trying to set up the home partition.  However, when I create it and set the mount point to "/home" despite choosing the maximum size (the remainder of my hard drive) it always resets the size of the partition to about 50GB.  Why is this?  Should I be setting it as a logical drive?

Also, what is the deal with /boot partitions?  Do I need one?

---

### Post by aeiah on 2007-06-25
ive had problems with resizing a home partition before where i would resize it, but it would refuse to acknowledge that it was bigger than a certain amount. are you setting these partitions up with the partition manager program (gparted) from the livecd? i solved my issue by downloaded the gparted livecd, which contains a newer version of gparted, and doing it from there. the cd image is only about 50mb and i find it pretty useful. it also boots quicker since its so small.

another issue might be that you're partitioning with 3 logical partitions. perhaps you could try creating an extended partition for /home, and then creating the /home partition inside it.

dont worry about /boot partitions and suchlike, they aren't needed, it just preserves your boot settings if you choose to reinstall but ive never found it to be too useful, since all available operating systems will be added to grub on a reinstall anyway.

---

### Post by insane_alien on 2007-06-25
i don't know what could be causing it but i can tell theat your swap partition is overly massive. are you on 64-bit? if your not then you won't be able to use it all anyway. the space would be better allocated elsewhere.

---

