---
title: "One quick question..."
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Epis0de on 2007-03-23
Guys...is there anyway to TOTALLY clean all partitions so I can restart an Install?

I think I messed up the install first time around as the GRUB error is showing.

(also how long should I be prepared to wait on the "grub loading..." sign at startup?

---

### Post by nudnik on 2007-03-23
> **Epis0de said:**
> Guys...is there anyway to TOTALLY clean all partitions so I can restart an Install?

I think I messed up the install first time around as the GRUB error is showing.

(also how long should I be prepared to wait on the "grub loading..." sign at startup?

There is a DOS program called KILLDISK which you can download for free from the Active software site that should do the trick. I recommend this only if you want to wipe the entire disk down to a nearly factory fresh state, otherwise, use one of the many fine Linux partitioning tools.

Grub takes about a second or so on my system. If it hangs for some time, something is probably broken, possibly the user (sorry, couldnt resist) :)

---

### Post by Epis0de on 2007-03-23
Yah yah yah, my computers not factory built, made it with my grandfather a year back, Its raided with nvidia stripe and the Ubuntu install didnt give me the option to wipe the whole drive, was determined to get me to put it on a single partition.

---

### Post by jhenager on 2007-03-23
Gparted will do that for you, as well as other similar utilities like Partition Magic.

Also, there is a free dos util called AEFDISK you can google/download/extract to a floppy.

Command line is C:\aefdisk -delall

Everything will go bye-bye, so make sure that's what you want.

---

### Post by Epis0de on 2007-03-23
God I wish this was easier

---

### Post by steve.horsley on 2007-03-23
LOL. It's easy when it goes right. It's just really hard when it goes wrong. Perhaps best is to just delete all the partitions with a live CD and let the installer start with a clean disk.

As for how long you should wait for the GRUB Loading... - well you really shouldn't have time to read it.

---

### Post by j002 on 2007-03-23
Maybe I'm missing something here but wouldn't getting a Windows bootdisk from Bootdisk.com, using DOS Fdisk to remove the partitions and then formatting do the job ?

Linux seems to install fine over a DOS/Windows disk, but I haven't had much luck using the partitioners they have on the install, for some reason they also seem to miss a small DOS/Win partition at the front of the drive so GRUB doesn't work.

---

### Post by Epis0de on 2007-03-23
Nope nope nope, this is partitioned with SATA raid 1 ( I think its 1- Certainly striped), kill me please.

---

