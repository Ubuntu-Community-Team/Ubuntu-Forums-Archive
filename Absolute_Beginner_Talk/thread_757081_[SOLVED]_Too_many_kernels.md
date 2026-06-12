---
title: "[SOLVED] Too many kernels"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by dwally89 on 2008-04-16
Hi,

By a mistake I have installed a few extra kernels, and I'm not sure how to remove them.
My GRUB lists:
Ubuntu 8.04, kernel 2.6.24-16-386
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-12-generic

How can I get rid of these kernels (not just from GRUB, but from my computer altogether)?

Thanks

---

### Post by wannadumpwindows on 2008-04-16
I'm with you. After numerous updates and such, I have a list of about 8 of them at boot. I only use the most recent one, so there's no need to have all the others hanging around for nothing. I'd be interested in knowing how to get rid of them too . . . . .

---

### Post by lswest on 2008-04-16
same way you remove any programs, use Synaptic or apt-get to remove the packages you want to get rid of.  At least, i assume so, i'm only using the 2.6.24-12-generic kernel, since the newer ones lost support for bcm4311 rev 2 and so i'm hoping they'll fix it by the release of the actual Hardy, and if not, well, i'll just ndiswrapper the drivers again.

---

### Post by dwally89 on 2008-04-16
I have the QGRUBEditor which allows me to remove entries from GRUB, however I don't know which entries to remove, and I don't know how to actually uninstall these extra kernels from my system (using synaptic)

---

### Post by philinux on 2008-04-16
Try startupmanager from synaptic. it has an option of how many kernels to display.

---

### Post by lswest on 2008-04-16
well, the entries you want to remove are those pertaining to the old kernel (generally, keep the recent kernel, and one version before that, just in case) and in synaptic search for 2.6.24-12-generic (for example) and mark the packages that refer to kernel images and such for removal.  However, if you don't require the disk space, best to just remove the entries from GRUB.

---

### Post by dwally89 on 2008-04-16
But i'm confused as to why I have the 386 kernel and the generic kernel.

Which one should I use?

Thanks

---

### Post by Bubba64 on 2008-04-16
I removed some of the extra kernels after a Hardy up date on my laptop but went to far and had to drop the whole distribution and go back to Gutsy for now due to a constant freeze up problem preceding the kernel removal, Be careful if you have stuff on your distribution that you can't  afford to lose. Back up all your stuff.

---

### Post by dwally89 on 2008-04-16
So do I use 386 or generic?

---

### Post by lswest on 2008-04-16
you can use either, generic has files that runs on all architectures (AMD64/i386/ppc, etc) and the -386 one has other features that might work better for your architecture (i386).  However, the generic (i believe) is required, whereas the others are optional.  So install -generic and keep the -386, but chances are you will physically **use** the -386 files.

---

### Post by dwally89 on 2008-04-16
Thanks

---

### Post by lswest on 2008-04-16
anytime.  Just want to point out, what i said before (though it may seem like i'm 100% sure) is just what i think, i could be wrong about anything i said above.

---

