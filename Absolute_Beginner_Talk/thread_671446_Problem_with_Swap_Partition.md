---
title: "Problem with Swap Partition"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by stefanonardi on 2008-01-18
Hi!

I'm definitely a newbie, both with Linux and English :)

Last week I tried to install Xubuntu on my HDD: everything went all right, I created an EXT3 and a swap partition after having resized an existing NTFS partition. As I found Xubuntu not too fast on my old PC (Via EPIA Mini-ITX 933MHz,RAM 512MB) I decided to try Slackware and I installed Vector Linux... Before installing, I read on a forum (don't remember which one) that multiple Linux OS can share the same Swap Partition, and creating a new one would be a waste of space.... then I resized the NTFS partition again and I told Vector Linux to use a new (reiserfs) partition AND  the existing Swap Partition created for Xubuntu.

The problem is the following: using Grub both VL and Xubuntu work, BUT if I try to Hibernate my current Xubuntu session, I get an error (don't remember, but I can check if needed) about failure to write on Swap Partition and, after pressing a key, I get back to Xfce again... as for me, it means what Xubuntu currently is NOT USING the swap partition! I can still find swap partition in /etc/fstab ...

How can I format the swap partition (the existing one) in order to let Xubuntu use it again, without reinstalling Xubuntu?

Thank you very much for your time, and hope someone could help me!

Best regards, 

Ste

---

### Post by zakirs on 2008-01-18
hi there is a swap file creating program which creates a file on haarddrive to use use as swap try to use it...
its name is dphys-swapfile

---

### Post by jeffus_il on 2008-01-18
If you are going to hibernate, you cannot share the swap partition, make two swap partitions. Normally the swap partition is only in use when an OS is running,   but hibernation writes the computer volatile memory to the swap partition, therefore it is needed between boots,  You have an option also of using a swap file in one of the installations, so you don't necessarily need two partitions as such, OK?

By the way, your English is perfect.

---

### Post by stefanonardi on 2008-01-21
> **jeffus_il said:**
> If you are going to hibernate, you cannot share the swap partition, make two swap partitions. Normally the swap partition is only in use when an OS is running,   but hibernation writes the computer volatile memory to the swap partition, therefore it is needed between boots,  You have an option also of using a swap file in one of the installations, so you don't necessarily need two partitions as such, OK?

By the way, your English is perfect.


Problem solved :)

Thank you very much, zakirs & jeffus!

Best regards,

Ste

---

