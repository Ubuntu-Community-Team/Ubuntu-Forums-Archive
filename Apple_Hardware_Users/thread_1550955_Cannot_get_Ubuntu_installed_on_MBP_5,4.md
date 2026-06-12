---
title: "Cannot get Ubuntu installed on MBP 5,4"
date: 2010-08-11
forum: Apple Hardware Users
---

### Post by sandhuatub on 2010-08-11
FC13 and Ubuntu 10.04 - both 64bit.
Hardware: MBP 5,4

Here's how I do the install:
1. Boot to Ubuntu LiveCD and wipe disk.
2. Create a msdos partition table via gparted
3. Reboot from FC13 or Ubuntu install disk and continue to install with installer suggested partition scheme.
4. Reboot and get an error that says "uncompression error -- System halted"

Variation that I have tried:
1. After #3, boot into FC13 or Ubuntu rescue mode, chroot to hd image and run:
# grub
> root (hd0,0)
> setup (hd0)
> quit 

Same result.

2. Create a 250MB partition where I installed refit and use rest of the  disk for Ubuntu or FC13. After installation, both Ubuntu and FC13 halt  at the same error.

3. gptsync fails with no refit installed. Finds GPT table empty.

LiveCDs from both distros work fine so ruling out hardware issues like bad memory etc.

---

### Post by sandhuatub on 2010-08-11
Tried Mandriva and same result - "Uncompression Error - System Halted"

---

