---
title: "fsck failed"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by yoramdavid on 2005-11-07
Hello,
I know similar threads have been posted, but none mach exactly mine and the answers did not help me. :confused:
When I boot into Ubuntu (I have also Windows XP & 98) with grub doing the booting, I get the following messages:
OT: clean failed
fsck failed
Press Ctrl+D to continue with normal boot.

When I do so it boots normally.
What is the problem?
How can I solve it?
I have heard of using the fdisk, but I do not want to change any partition from linux otherwise my windows installations will go funny.
I have hda and hdb, both with several partitions.

Thanks for the help.
Yoram David

---

### Post by ubuntu_demon on 2005-11-07
during boot press esc to get into grub. Try to boot in recovery mode  and see if it starts to correct your filesystem. After booting type "restart" and see if the problem is gone the next time you boot.

---

### Post by Mustard on 2005-11-07
If you find the error doesn't go away, I would say you will need to use fsck from a liveCD, as fsck can't fix a mounted partition.  It necessary for the partition to be unmounted.  If its your main linux partition then that will be problematic without the help of a liveCD.

---

### Post by az on 2005-11-07
[QUOTE=Mustard]If you find the error doesn't go away, I would say you will need to use fsck from a liveCD, as fsck can't fix a mounted partition.  It necessary for the partition to be unmounted.  If its your main linux partition then that will be problematic without the help of a liveCD.[/QUOTE]
On boot, fsck is run from the initrd, so the filesystem is not mounted....

I would say that you have a bad sector.  Can you create another partition and copy your data there?

---

