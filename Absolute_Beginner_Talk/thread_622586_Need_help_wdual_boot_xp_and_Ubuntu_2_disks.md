---
title: "Need help w/dual boot xp and Ubuntu 2 disks"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by BrunoBB on 2007-11-24
Current setup is:
XP on master disk
Suse 10.1 on slave disk
Grub on master disk (allows for dual booting)

What I want is:
XP on master disk (hda)
Ubuntu (7.10) on slave disk (hdb)
Grub on master disk (with the option to dual boot XP and/or Ubuntu)

Questions: 
I need some help with the install - step 4 to be exact.  Do I select "Guided - Use entire disk" and then select my slave disk (hdb) ???

Will the install process take care of updating my existing Grub menu???

Thanks in advance.

---

### Post by Danikar on 2007-11-24
I would select manual.

Then you can just parition your slave disk as needed.

Probably just a / and a swap.

Oh I didnt read the grub part.  Maybe you could do.

/media/hda1 NTFS
/media/hda1 /boot

/media/hda2 /
/media/hda2 swap

But I would double check with one of the smarter ones. =)

---

### Post by alienexplorers on 2007-11-25
I have XP on hda1 and ubuntu on hda2.  I have hda2 partitioned with a root / partition, /home partition and swap partition.  I allowed grub to overwrite the MBR on the hda1 drive.  I have no problems booting windows and ubuntu with this setup.

---

### Post by meierfra on 2007-11-25
> Questions:
I need some help with the install - step 4 to be exact. Do I select "Guided - Use entire disk" and then select my slave disk (hdb) 

That should work just fine,

> Will the install process take care of updating my existing Grub menu?

Yes, actually it will replace it by a new one.

The only reason to choose "manual" would be to create a separate /home partition.

---

### Post by BrunoBB on 2007-11-25
I selected "Use entire disk" on my slave drive and Ubuntu took care of updating Grub.

Very painless, I love it!!!

Thanks to all who responded.

Bruno

---

