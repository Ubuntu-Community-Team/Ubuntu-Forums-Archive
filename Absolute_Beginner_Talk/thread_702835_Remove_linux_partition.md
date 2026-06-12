---
title: "Remove linux partition"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by reeksy on 2008-02-20
Hi

I want to reinstall Ubuntu 7.10 as I've had a few problems with it (my fault). I've just downloaded Partition Magic 8 and i have the following Disks:

Local Disk (C) NTFS
Local Disk (*.) Linux Ext3
(*) Extended
SWAPSPACE2 (*.) Linux Swap

Am i correct in thinking i can delete the following three partitions to safely return to the Windows single boot?

Local Disk (*.) Linux Ext3
(*) Extended
SWAPSPACE2 (*.) Linux Swap

(This will leave me with the sole NTFS partition)

From there, i'll the pop in the Live CD again and start over!

Regards.

---

### Post by zerhacke on 2008-02-20
If you remove the Linux partitions and want to boot Windows before you reinstall Ubuntu you're going to need your Windows setup CD to log in to the recovery console and fixmbr fixboot.

Otherwise, yeah, you can just delete the partitions and recreate them with your Ubuntu cd.

---

### Post by spiderbatdad on 2008-02-20
not quite that easy, but wait for some other opinions. I think you first need to repair the master boot record on windows with your disk (or recovery program) in recovery mode run fixmbr. Defrag your windows installation. Then start from scratch with the Gutsy cd.

---

### Post by reeksy on 2008-02-20
> **zerhacke said:**
> Otherwise, yeah, you can just delete the partitions and recreate them with your Ubuntu cd.

OK, so would you delete the partitions using the Live CD or Partition Magic?

---

### Post by robkeys on 2008-02-20
I'd use the live cd, what with it being free and open source and all ;)

---

### Post by Duck2006 on 2008-02-20
> **reeksy said:**
> OK, so would you delete the partitions using the Live CD or Partition Magic?

Use the live CD and open the partition editer and do it all from there, you don't need partition magic 8, the live CD uses gparted to do it with.

---

### Post by Shazaam on 2008-02-20
Why delete the partitions? Just point the livecd installer to the current Ubuntu partitions and it will overwrite whatevers there. Just make sure you write down the partition names first (hda1, sda3 etc) so you don't accidently format the Windows partition.
Such as this=
hda1=Windows
hda2=Ubuntu
hda3=swap
etc.

---

### Post by zerhacke on 2008-02-20
> **spiderbatdad said:**
> not quite that easy, but wait for some other opinions. I think you first need to repair the master boot record on windows with your disk (or recovery program) in recovery mode run fixmbr. Defrag your windows installation. Then start from scratch with the Gutsy cd.

> **zerhacke said:**
> If you remove the Linux partitions and want to boot Windows before you reinstall Ubuntu you're going to need your Windows setup CD to log in to the recovery console and fixmbr fixboot.

Otherwise, yeah, you can just delete the partitions and recreate them with your Ubuntu cd.

That's what I just said.

---

### Post by reeksy on 2008-02-21
> **Shazaam said:**
> Why delete the partitions? Just point the livecd installer to the current Ubuntu partitions and it will overwrite whatevers there. Just make sure you write down the partition names first (hda1, sda3 etc) so you don't accidently format the Windows partition.
Such as this=
hda1=Windows
hda2=Ubuntu
hda3=swap
etc.

Thanks, i'll try this now.

---

