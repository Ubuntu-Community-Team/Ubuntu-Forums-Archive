---
title: "Linux icon in rEFIt boots winders partition.."
date: 2008-01-02
forum: Apple Intel Users
---

### Post by Mua'dib on 2008-01-02
I have a triple-boot setup on two drives in a Mac Pro. On the first drive is a efi partition, 2 HFS+ partitions (boot & user_files), a etc3 / boot partition, and a swap partition. On the second drive is a efi partition, a HFS+ boot partition and a NTFS (BootCamp) Winders partition.
I first reformatted the first drive w/ dskutil to set up its partitions. Fresh Leopard install on the first drive and then installed rEFIt. Then used BootCamp to repartition the second drive.
Next was the Winders XP install, which went fine. rEFIT showed OSX, OSX, and Winders.
When I went to install Ubuntu 7.10 on the first drive, it didn't like the 2 efi partitions, so I removed the 2nd drive and the install went well. I installed the Grub to the boot partition (/).
With the 2nd drive removed, the rEFIt menu showed OSX and Linux. rEFIt worked fine - I could boot into OSX or Ubuntu. When I reinstalled the second drive, rEFIt showed OSX, Linux, OSX, and Winders, but the Linux icon boots Winders instead of Ubuntu.

How do I fix this?

---

### Post by cyberdork33 on 2008-01-02
there are some other threads on this. Grub sees devices oddly on a Mac (or EFI in general, or whatever) for some reason. From what I have seen, most are trying to install Ubuntu on the second drive by itself, and it has issues upon trying to boot, but editing the grub config files to show Ubuntu as being on the primary, first, hard drive gets things working. It is as though grub sees the last drive as the first, and the first as the last... something like that. I do not have any firsthand experience, but there are those here that have gotten it working someway or another.

Sorry I can't help you more. It is a strange and confusing issue.

---

