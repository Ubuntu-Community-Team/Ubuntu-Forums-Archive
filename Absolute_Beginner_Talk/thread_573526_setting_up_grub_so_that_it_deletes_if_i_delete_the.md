---
title: "setting up grub so that it deletes if i delete the linux partition"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by PharaohSD on 2007-10-11
hiya,

was wondering how to set up the partitions so that when i install ubuntu and partition my main hd0 into

/media/ whatever *vista
/media/ whatever *hp recovery partition
/ *main ubuntu install
/swap *swap

i would install grub in /   and when I want to delete linux I could just delete the / and /swap partitions and my computer would automagically revert back to the original boot loader **(without having to get the vista install cd and doing the /FixMbr command)**


so the question is, where do i put the grub boot loader (during manual install)  and i still have to enable the boot flag in / right?   

is this even possible?

thanks

---

### Post by Kilz on 2007-10-11
No

---

### Post by steve.horsley on 2007-10-11
It is possible to install GRUB onto the root partition, but then you will still need a different bootloader on the disk MBR to boot the root partition. If you intend to dual-boot with Vista then I guess you're looking at using the Vista bootloader. 

The Ubuntu installer gives you the option of installing GRUB to somewhere other than the MBR, you just have to tell it which parition. For reference, /dev/hda2 would be known to grub as (hd0,1), or ws it hd(0,1) - can't remember which but drives and partitions number from 0 in GRUB.

I believe Windows bootloaders can be persuaded to boot other partitions but I don't know how.

---

