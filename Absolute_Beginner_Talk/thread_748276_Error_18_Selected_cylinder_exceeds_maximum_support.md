---
title: "Error 18: Selected cylinder exceeds maximum supported by BIOS"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by brjoon1021 on 2008-04-07
Hi,

I have Gutsy installed on a 160 GB IDE disk along with Win XP. GRUB is in the MBR. The first partition, the XP NTFS one, is 90 GB. Gutsy is on a ReiserFS on the rest of the disk.  The motherboard is very current with the latest BIOS. The 137GB boundary is not an issue, it is not even crossed, anyway. I checked my BIOS it is set properly for the way an IDE disk should be set, as far as I understand it.

This error message occured after a Gutsy Lockup. I had to shut the system down by the power supply. Now, I get this error after selecting Ubuntu with GRUB. Windows boots just fine from GRUB.

Any ideas?

---

### Post by pseudo-random on 2008-04-07
Check your BIOS settings for that particular HardDrive.
 It'll have Auto, LBA, etc Try something different. If your BIOS is good it'll let you manually specify the cylinders per head etc though I would advise you not to touch this.
Normally Auto will suffice but sometimes you've got to change it to LBA or similair.

---

### Post by wolfen69 on 2008-04-07
i found this:

Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot. [http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)

---

