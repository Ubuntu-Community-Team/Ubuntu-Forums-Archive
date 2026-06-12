---
title: "Update USB Multiboot"
date: 2012-06-21
forum: Any Other OS
---

### Post by neuman1812 on 2012-06-21
I have backtrack 5 installed on a USB using the 'multiboot' program.  I was wondering if there is anyway to install changes/updates to backtrack while Im booted on the USB?

it appears that backtrack is running as a LiveUSB  so any changes I make are not saved.

---

### Post by C.S.Cameron on 2012-06-21
I would not run update on a Live system.
It will quickly fill your drive.
You can replace the BT iso with a new one of the same name.
Or you might be able use Remastersys to make an updated iso, (I have not tried with BT).
You can make the multiboot persistent by adding a casper-rw file or partition.
Note that you should only have one distribution on the multiboot disk using the casper-rw.

---

