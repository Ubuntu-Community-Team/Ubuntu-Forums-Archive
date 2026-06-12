---
title: "Backtrack 5 persistent USB"
date: 2013-08-13
forum: Any Other OS
---

### Post by karl4 on 2013-08-13
Hello to All. 

I am unable to boot into persistent mode from a USB drive that I recently created with Lily USB Creator. I can boot into the Backtrack Text Mode when I press tab and edit the command line to include the option: i915.modeset=1. If I don't I include this option, I get a black screen after using the startx command. If I try to add this same option to the command line after choosing Persistent mode, I get  the error -->  (initramfs):mounting aufs on /root failed; Invalid argument aufs mount failed.  Here are the command line options for Persistent Mode:
[CENTER]
/casper/vmlinuz file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz persistent cdrom-detect/try-usr=true text splash vga=791--[/CENTER]

Can I add the option i915.modeset=1 to this line (I suspect not) or must I edit a file?  I have posted here because the Backtrack 5 forums are closed since the release of Kali Linux.
Can you guys help? Thanks

---

### Post by C.S.Cameron on 2013-08-15
Do you have a casper-rw persistent file or folder?

If not try installing using UNetbootin with extra space.

---

