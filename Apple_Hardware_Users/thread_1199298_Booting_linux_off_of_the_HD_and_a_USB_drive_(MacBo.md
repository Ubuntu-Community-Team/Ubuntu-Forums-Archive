---
title: "Booting linux off of the HD and a USB drive (MacBook 4,1)"
date: 2009-06-28
forum: Apple Hardware Users
---

### Post by rabid_gnome on 2009-06-28
My current partition scheme is
[EFI][OS X][Ubuntu 9.04][Windows XP]
using rEFIt, and everything with this set up works properly to the best of my knowledge.

My problem is that I wanted to boot kubuntu off of a 60G usb drive, which is not working properly. The installation goes fine (installing grub to /sdb), but when I use rEFIt to boot the USB drive it loads the grub menu for Ubuntu (installed on /sda2).

I was wondering if anyone has been able to get grub to load from a USB drive like I would like it to.

---

### Post by pxwpxw on 2009-06-29
> **rabid_gnome said:**
> My current partition scheme is
[EFI][OS X][Ubuntu 9.04][Windows XP]
using rEFIt, and everything with this set up works properly to the best of my knowledge.

My problem is that I wanted to boot kubuntu off of a 60G usb drive, which is not working properly. The installation goes fine (installing grub to /sdb), but when I use rEFIt to boot the USB drive it loads the grub menu for Ubuntu (installed on /sda2).

I was wondering if anyone has been able to get grub to load from a USB drive like I would like it to.

grub1-pc cannot boot external drive on a Mac.
External needs grub.efi, see grub2 efi bootloader thread
Post #772 grub-efi64.tar.gz

---

