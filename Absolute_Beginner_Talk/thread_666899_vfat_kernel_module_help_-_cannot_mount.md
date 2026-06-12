---
title: "vfat kernel module help - cannot mount"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by infinite regress on 2008-01-13
Hello everyone.

I recently compiled a new kernel, and I seem to have taken out the support for vfat filesystems. I'm not quite sure how I can get it back...

I tried compiling the modules again with the vfat support as a module, but my usb stick still won't load.

Any ideas?

thanks.

---

### Post by blueridgedog on 2008-01-13
When you installed the new kernel, I assume you preserved the other kernels as boot option.  Is the USB drive working in those kernels?

---

### Post by infinite regress on 2008-01-13
Oh. MY GOD... 
Oh ok. Yeah, it mounts on the original kernel... I'm not too fussed about getting it working on the new kernel now, I just had files on my usb that i didn't want to lose.

Just out of interest.. When I compiled the new kernel, I lost about a gig of hard drive space. How do I get rid of the old kernel and get that space back?

THANKS!

---

### Post by blueridgedog on 2008-01-13
I would assume the gig of space if for the sources you downloaded.  You could sudo apt-get remove them, but I would leave it.

The consensus is that generic kernels, with the ample module support and the cpu sensing, are nearly as good as a home rolled kernel.  Why did you want to compile one other than for the fun and experience?

---

### Post by infinite regress on 2008-01-14
I had drivers that would only compile on 2.6.23+ kernels, and I had to complie. Turns out, the drivers wouldn't compile anyway, so it was a bit of a waste. Boot up is slower too...

I've made a mess of this install, so I'll reinstall in a few weeks anyway...

Thanks for your help!

---

