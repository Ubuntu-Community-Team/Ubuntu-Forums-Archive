---
title: "EFI boot loader information"
date: 2011-09-23
forum: Apple Hardware Users
---

### Post by srs5694 on 2011-09-23
If anybody is interested, I've recently created a new set of Web pages on EFI boot loaders for Linux:

[http://www.rodsbooks.com/efi-bootloaders/index.html](http://www.rodsbooks.com/efi-bootloaders/index.html)

I describe my experiences with ELILO, Fedora's patched GRUB Legacy, GRUB 2, and rEFIt on those pages. The rEFIt page also provides a patched version of rEFIt that enables hiding the legacy (BIOS) options, which might be useful if you're using an EFI-only boot strategy and your rEFIt configuration is displaying bogus BIOS boot options. This feature won't be useful if you triple-boot with Windows, though, since Windows boots using BIOS mode.

---

### Post by the-ridikulus-rat on 2011-09-24
Did you checkout [http://git.kernel.org/?p=boot/efilinux/efilinux.git;a=summary](http://git.kernel.org/?p=boot/efilinux/efilinux.git;a=summary) (temporarily at [https://github.com/mfleming/efilinux](https://github.com/mfleming/efilinux) ) and [https://groups.google.com/group/linux.kernel/browse_thread/thread/9aac8bf3b646bf62/f0963b50a956f3d9?lnk=gst&q=x86+EFI+boot+stub#f0963b50a956f3d9](https://groups.google.com/group/linux.kernel/browse_thread/thread/9aac8bf3b646bf62/f0963b50a956f3d9?lnk=gst&q=x86+EFI+boot+stub#f0963b50a956f3d9) (based on efilinux, efilinux will be gone once the boot stud is stable).

---

### Post by the-ridikulus-rat on 2011-09-24
When grub-legacy efi app is launched, it checks the filename and path of the launched efi app and tried for ${that_filename}.conf , ie. incase of redhat.efi will try only redhat.conf , does not try grub.conf (not even fallback on grub.conf file even if it exists in the same dir as redhat.efi). This behaviour is not exhibited by grub2.

EFILINUX did not load Archlinux x86_64 kernel and initramfs (version 3.0.4) properly in UEFI 2.3.1 EDK2 DUET x86_64. 

Also grub2 has problems in UEFI systems using 8 GiB or more RAM [https://lists.gnu.org/archive/html/grub-devel/2010-04/msg00178.html](https://lists.gnu.org/archive/html/grub-devel/2010-04/msg00178.html) . Both these problems are caused by different memmap issues. Seems like grub2 8 GiB  issue is due to buggy firmware.

---

### Post by srs5694 on 2011-09-24
Thanks for the pointers, skodabenz! I'd heard some vague things about kernel-based boot loader, but I didn't have any details. I'll check into the GRUB Legacy configuration file naming issue and the GRUB 2 8 GiB RAM limit and update my pages as necessary.

---

