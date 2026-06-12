---
title: "Quick External HD question"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Hypnotik on 2008-02-18
I have the drive mounted and the OS recognizes it.  If I unplug it (USB) and plug it back in do I need to do any configuring or will it be mounted in the same spot?

Thanks,
jeff

---

### Post by az on 2008-02-18
If you mounted it by hand, no.  If it was mounted by HAL (Hardware abstraction layer), and the Gnome-Volume-Manager, then it should be mounted again in the same spot. as long as you do not plug in anything else before.

If you add an fstab entry for your drive, and specify the UUID of the filesystem, then it will be mounted in the same spot every time.

---

### Post by Hypnotik on 2008-02-18
All I did was plug the drive in and the icon popped up on the desktop.  I'm assuming that is NOT what you mean mounting by hand.  I'm pretty new to Ubuntu/Linux so I'm not completely sure how to do the fstab stuff...and not completely sure what the UUID is.  Is that the file system...such as FAT32?

Thanks for the help,

Jeff

---

