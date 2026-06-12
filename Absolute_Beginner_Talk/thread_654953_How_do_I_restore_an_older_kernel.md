---
title: "How do I restore an older kernel?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Antarctica on 2007-12-31
I tried to follow an older tutorial on getting my Microsoft Natural Ergonomic Keyboard 4000 working, but I came to a step that I couldn't find the solution to.  In the process I had to download a generic kernel, the 2.6.22-14-generic.  Anyway, it caused my computer to crash after GRUB boots.  I was able to boot into the Live CD and copy the /boot directory from the CD to /media/disk/boot (the boot directory on my hard drive).  The kernel I want to get rid of is still installed in /usr/src/linux.  How can I get the kernel from the Live CD back onto the hard drive, and then do I need to recompile everything under the Live CD's kernel, and if so, how do I do that?  Thanks.

---

### Post by Majorix on 2007-12-31
The older kernel should still be available to you.

While booting, in the grub menu, choose the older kernel. You should now boot into it.

While in it, edit your /boot/grub/menu.lst, scroll to the end and remove the generic kernel entry or make something else the default.

Hope it helps.

---

### Post by Antarctica on 2007-12-31
The generic kernel shows under the GRUB boot menu.  I want to restore the one that is on the CD.  How do I do that and recompile everything under the CD's kernel?

---

### Post by Majorix on 2007-12-31
You don't get the other kernels as options? Only the generic one?

---

### Post by Antarctica on 2007-12-31
No I get only two options, the generic one and then the recovery one.  Also, I am running Ubuntu 7.10 Gutsy AMD64, so I need the AMD64 kernels.

---

