---
title: "PPC install successful, first reboot, firmware cannot recognize new OS"
date: 2012-05-01
forum: Apple Hardware Users
---

### Post by p4lmtree on 2012-05-01
I have an old PowerPC G4 desktop. I installed with the alternate CD, and everything went smoothly during installation.

When the computer rebooted for the first time, the new OS would not load.  Instead, I got the blank screen with the folder icon, flashing between the "Mac face" and a question mark.  IIRC, this means the firmware is trying to load OS X and cannot find it on the HDD.

Is there anything I can do to make Lubuntu boot on startup? The only thing I can think of is holding Command-O+F on startup to boot into the firmware, then type some command....whatever that may be.

---

### Post by rsavage on 2012-05-02
See FAQ for how to boot [https://wiki.ubuntu.com/PowerPCFAQ#I.27ve_lost_yaboot.2C_what_can_I_do.3F](https://wiki.ubuntu.com/PowerPCFAQ#I.27ve_lost_yaboot.2C_what_can_I_do.3F) 
 
But... 
 
Did you really not get any errors during install? Are you using a large hard drive (i.e. much bigger than the standard one that came with the machine)? See [https://wiki.ubuntu.com/PowerPCFAQ#What_partitions_do_I_need_etc.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_partitions_do_I_need_etc.3F)

---

### Post by p4lmtree on 2012-05-02
> **rsavage said:**
> 
 
Did you really not get any errors during install? Are you using a large hard drive (i.e. much bigger than the standard one that came with the machine)? See [https://wiki.ubuntu.com/PowerPCFAQ#What_partitions_do_I_need_etc.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_partitions_do_I_need_etc.3F)

Yeah, I got absolutely no errors, which kinda surprised me.  My HDD is only 80GB.  I don't know if it came with the computer or not. During the partition I chose to use the entire disk (first choice).

I'll try the OF commands in the FAQ you sent me.  The examples in the FAQ seem to be particular to partition 3, but I don't know for sure if I even have three partitions since I chose to use the entire disk:

```

hd:3,/boot/vmlinux --no-log

hd:3,/boot/vmlinux.old

```

What do you think?

---

