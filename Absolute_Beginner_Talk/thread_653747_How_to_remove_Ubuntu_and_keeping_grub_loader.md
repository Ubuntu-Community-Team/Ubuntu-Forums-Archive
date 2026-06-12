---
title: "How to remove Ubuntu and keeping grub loader"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-12-30
If i have ubuntu sharing with vista on a pc, usually when i delete the whole ubuntu partition the next time i restart my pc, ill run into a black screen showing some error which doesn;t allow me to even load windows, can anyone help?

---

### Post by LaRoza on 2007-12-30
See the link in my sig, get the Super Grub Disk and boot from it.

Advanced->Windows(Advanced) and restore the boot loader.

---

### Post by the_nomad on 2007-12-30
you can install vista again and the grub will certainly disappear but that's just a noobish advice sorry :)

---

### Post by LaRoza on 2007-12-30
> **the_nomad said:**
> you can install vista again and the grub will certainly disappear but that's just a noobish advice sorry :)

Actually, if the OP has the Vista install disk, you can restore the MBR with the command "fixmbr".

Install disks for Vista are rare though.

---

### Post by kinngg on 2007-12-30
so laroza if i boot from the cd it wouldn't remove my windows? because i lost my windows cd key so if i delete my vista it would be gone forever :(

---

### Post by erfahren on 2007-12-30
it would be much easier to fix it before deleting the Linux partition
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by LaRoza on 2007-12-30
> **kinngg said:**
> so laroza if i boot from the cd it wouldn't remove my windows? because i lost my windows cd key so if i delete my vista it would be gone forever :(

If you use the Super Grub Disk, you will only be able to boot Windows. From Windows, you can safely delete Ubuntu from the Computer Management -> Disk Management

You can grow the Vista partition to fill the space.

---

### Post by mc4man on 2007-12-30
while I don't and never will have vista i remember seeing this prog. while researching something for a friend - looks like it could be useful for vista users (not necessarily op)
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by yaknowwat on 2007-12-30
GRUB Requires a linux style partition if you plan to use it so you know.
So I suggest making a 64 MB ext2 partition with a live CD then installing GRUB to that.

A work around for this problem is instead of doing a full delete of the Ubuntu Partition use a live CD and delete everything except the ' /boot ' directory then resizing the partiton to about 64 MB (can be smaller though its always good to leave extra space)

Also while on the live CD you may want to alter what the /boot/grub/menu.lst says like deleting ubuntu option's changing the default if necessary.

Anyways the problem is that the MBR is pointing to GRUB on the non-existent partition (as you just deleted it).

---

