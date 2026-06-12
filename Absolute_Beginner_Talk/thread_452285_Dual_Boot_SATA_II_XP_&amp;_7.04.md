---
title: "Dual Boot SATA II XP &amp; 7.04"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by clipper74 on 2007-05-23
I have the following setup which I'm trying to get dual booted;

4 SATA II disks,
  1 - 250GB WD with XP
  2 - 40GB general backup disk
  3 - 40GB with Ubuntu
  4 - 250GB Maxtor with my stuff on it, (music, photos etc)

Within the system BIOS, disk 1 is highlighted as disk 1 from the list of four and is therefore the one the BIOS will try to boot from. It is also the C:\ dirve of XP. It has NTLDR on its MBR and boots up XP.

disk 3 has grub in its MBR and when used as the boot disk, loads Ubuntu nicely, however grub knows the system holds an XP disk but as the NTLDR is not in the same MBR (remember it's on disk 1), XP booting fails.

I don't want to be moving disks around within the BIOS to make XP or Ubuntu the boot drive everytime I change the OS I'm booting. I really need grub on the same MBR as NTLDR. I would prefer grub to be on disk 1 besdie the NTLDR.

How do I do this? i need XP for work related things so moving to Ubuntu entirley is not an option just now.

Thanks.

---

### Post by neotasic1 on 2007-05-23
I don't understand why you think Grub needs to be in the MBR of disk 1.  I run a box with 6 Hdd's with two in a RAID array (IDE and SATA disks present)  My Ubuntu installation lives on its own physical hard drive XP on a different drive.  Both can be booted flawlessly from GRUB although to my knowledge, GRUB is installed on the Linux hard drive (I could be wrong as I don't know where physically GRUB is loaded, but this was how the default installation set it up, and it works, so I am curious as to how you managed your setup)

---

### Post by gn2 on 2007-05-23
> **clipper74 said:**
> 

I don't want to be moving disks around within the BIOS to make XP or Ubuntu the boot drive everytime I change the OS I'm booting. I really need grub on the same MBR as NTLDR. I would prefer grub to be on disk 1 besdie the NTLDR.



Can you bring up a boot device selection menu by pressing a Function button, sometimes F8 or F2?

If yo can,  just "point" the BIOS at the drive you want to boot from, without actually having to enter the BIOS and re-sort the boot order each time.

Failing that, this might help : [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

