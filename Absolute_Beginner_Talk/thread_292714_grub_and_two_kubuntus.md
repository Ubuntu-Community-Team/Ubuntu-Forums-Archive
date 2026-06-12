---
title: "grub and two kubuntus"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by pressman57 on 2006-11-04
Hi there.

I bought a brand new hard drive and set it up as slave, put an 80 gig partition on hdb1 and Kubuntu on hdb2. An older version of Kubuntu (breezy) lives on hda1:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4677 37567971 83 Linux
/dev/hda2 4678 4865 1510110 5 Extended
/dev/hda5 4678 4865 1510078+ 82 Linux swap / Solaris

Disk /dev/hdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 1 10199 81923436 83 Linux
/dev/hdb2 * 10200 19835 77401170 83 Linux
/dev/hdb3 19836 20023 1510110 5 Extended
/dev/hdb5 19836 20023 1510078+ 82 Linux swap / Solaris

When I installed Kubuntu Edgy, it looked for "other operating systems" and edited grub accordingly (hd0). I recently removed Edgy and put the partition into freespace, but when I tried to reboot the machine wouldn't recognize the grub file on hda1 (/boot/grub/menu.lst looked the same) and refused to boot. The bios only list "Hard Drive".

How can I boot directly into hda1?

---

### Post by Sef on 2006-11-11
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

