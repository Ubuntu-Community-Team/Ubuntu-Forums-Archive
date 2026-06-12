---
title: "Installing rEFIt does nothing. What's up?"
date: 2017-07-09
forum: Apple Hardware Users
---

### Post by sterator on 2017-07-09
I followed the extremely un-difficult instructions, rebooted my mac and saw no boot menu. Installed again, rebooted again. Nothing.

According to the directions, I should see a reboot menu upon reboot.

Any ideas how to correct this and properly instal rEFIt?

Thank you!

---

### Post by oldfred on 2017-07-09
I believe rEFIt has not been maintained, you probably need to use rEFInd which is an updated fork of rEFIt. 

 Alternative efi boot loader for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by kevin160 on 2017-07-11
Yep, you need rEFInd instead.  Don't forget that holding down the OPT key during startup on any mac lets you choose which partition to boot.  

As for UEFI, we call it EFI on macs, but Apple forked their own version way back in 2005 or so and it is not the same as UEFI found on modern PCs.  There is no EFI shell, and there is no concern over either "secure boot" or "legacy" boot modes.  Some things work, but take any UEFI guide with a grain of salt while working out mac boot issues.

---

