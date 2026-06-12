---
title: "Edgy splash in Parallels VM?"
date: 2006-10-28
forum: Apple PPC Users
---

### Post by hajk on 2006-10-28
Just installed Edgy (i386) in a Parallels VM on my MacBook 1.83GHz, 1MB RAM. Everything works fine, except there is no splash screen when booting or when closing down. Of course, I have enabled the 1280x800 native resolution in the VM and I tweaked xserver-xorg to select this instead of the default 1024x768 resolution. But this only works after booting, not during.
I wonder whether some additional boot options would work, like vga=...
Any ideas, anyone?

---

### Post by hajk on 2006-10-28
Answering my own query... the kernel boot option "vga=792" (to be added to /boot/grub/menu.lst) does the job (sort of).

Now, this gives the default 1024x768 splash image (as also specified in /etc/usplash.conf), which doesn't entirely fill the 1280x800 MacBook screen. But some splash image is better than none.

I would still be interested in getting a 1280x800 Edgy splash image -- once installed in the initramfs it would require kernel boot option "vga=869". Does anyone know how I can generate such an image?

---

### Post by DonnieP on 2006-10-31
My understanding of this is sketchy at best, but I don't think there's anything you can do to get splash past 1024x768.  It's up to the Ubuntu team to do that.  Maybe suggest it for Feisty?  I use an I*n*t*e*l iMac 1680x1050 running Ubuntu in Parallels and wound up at the same place you did with usplash.

---

