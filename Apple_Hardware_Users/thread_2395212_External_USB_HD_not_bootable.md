---
title: "External USB HD not bootable"
date: 2018-06-28
forum: Apple Hardware Users
---

### Post by chkneater on 2018-06-28
I am using a MacBook running 10.6.8 and I want to boot off an external USB HD but the partitins are marked "Not Bootable" by the Disk Utility even though I know the Ubuntu install is good as I've used it on different computers.  It also wont' mount the swap or Ubuntu partitins but it reads the NTFS partition fine.  Is this fixable running the Mac OS cuz it seems like an easy fix, just don't know how?...

---

### Post by oldfred on 2018-06-28
New systems & all Mac since they converted to Intel use UEFI, Mac is early version EFI with some updates.
If you were booting other systems in BIOS boot mode that may be the problem.
You Mac may have a special BootCamp mode for BIOS boot? I do not know Macs?

If external drive UEFI with gpt partitioning or BIOS with the now 35 year old MBR(msdos) partitioning?

You probably will need the Ubuntu live installer to make repairs. Or may need to convert to UEFI.
Post this:
sudo parted -l

---

