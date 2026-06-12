---
title: "Help with Toshiba A75 laptop."
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by perrybergmann on 2007-06-04
--------------------------------------------------------------------------------

I have no idea why it's happening, but I had the exact same error, and here's how I fixed it:

At the grub boot screen, use your arrow keys to highlight "kernel /boot/linuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash" (your exact paths and numbers might be a little dfferent). Then type 'e' to edit the boot options; you will be taken to another screen. Append 'noapic' to the end of the boot options, and hit enter. Then just type 'b' to boot. Dapper should then boot normally. 

To make these changes permanent, do the following:

I did this, but the options are as follows:

Ubuntu, Kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic(recovery mode)
ubuntu, kernel 2.6.20-15-generic
ubuntu, kernel 2.6.20-15-generic(recovery mode)

Which of these do I need to edit to change this around?

---

### Post by dstew on 2007-06-04
Edit the kernel line you use to boot in the /boot/grub/menu.lst file:```
sudo nano /boot/grub/menu.lst
```Just add noapic to the end of the line. If you boot the 2.6.20-16-generic kernel, put it into that line. To make this option "automagically" go into a new kernel menu.lst line when you update the kernel, add it to the #defoptions line in the upper part of the menu.lst file:```
#defoptions=quiet splash noapic
```

---

