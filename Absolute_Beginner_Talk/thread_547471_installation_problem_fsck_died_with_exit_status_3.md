---
title: "installation problem: fsck died with exit status 3"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2007-09-10
hi,
i'm trying to re-install ubuntu feisty. I've got two cds found in two magazines, but both give me the same result.
The problem is that after installing with success, when it reboots i get

* Checking root file system...
fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1: Superblock last mount time is in the future. FIXED.
/dev/sdb1: Superblock last write time is in the future. FIXED.
/dev/sdb1 has gone 49710 days without being checked, check forced.
/dev/sdb1: ***** REBOOT LINUX *****
/dev/sdb1: 98408/2064384 files (0.1% non-contiguous), 585723/4122680 blocks
fsck died with exit status 3

 * The file system check corrected errors on the root partition
 but requested that the system be restarted.
 * The system will be restarted in 5 seconds.

it reboots but when it runs fsck it works for some seconds, the hd's  led is on then it turns off and then 
nothing happens, fsck seems in loop.

It's the first time i install feisty from cd, before i updated it from 6.10.
What can i do to solve this problem?
thanks

---

### Post by BrendanM on 2007-09-10
The good news is that some Greek guy is having the same problem: [http://lists.hellug.gr/pipermail/linux-greek-users/2007-June/069049.html](http://lists.hellug.gr/pipermail/linux-greek-users/2007-June/069049.html)

The bad news is I don't read Greek.

Anyway, based on the timestamp errors, it sounds like maybe there's something wrong with your system clock?

If you can boot from the live CD, I would suggest doing that, and then running an fsck from the live CD. You might have better luck if you're not trying to run fsck from the disk that's being checked.

---

### Post by ubunlilluz on 2007-09-10
i found it too, but i don't understand greek too.

---

### Post by meindian523 on 2007-09-10
Try google translate.

---

### Post by ubunlilluz on 2007-09-11
now after thousands proofs it works, but i had to choose the predefinite partitions of ubuntu, thus  only root and swap. Before i had home too, but after 4 days of work am tired and i don't want to weist more time and strenghs. But i've a doubt wath is the disanvantages of kind of partitioning?
thanks

---

