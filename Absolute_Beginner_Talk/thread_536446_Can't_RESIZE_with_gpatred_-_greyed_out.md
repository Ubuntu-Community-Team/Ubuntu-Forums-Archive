---
title: "Can't RESIZE with gpatred - greyed out"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by bliffle on 2007-08-27
I can't seem to get the RESIZE option enabled. Plugged this HDD USB into the USB, just like last week, Started gparted with "sudo gparted" but the RESIZE option is greyed out.

Am I missing a mount of some kind or a fstab or mtab entry?

---

### Post by Duck2006 on 2007-08-27
Try the live CD og gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by jimrz on 2007-08-27
> **bliffle said:**
> I can't seem to get the RESIZE option enabled. Plugged this HDD USB into the USB, just like last week, Started gparted with "sudo gparted" but the RESIZE option is greyed out.

Am I missing a mount of some kind or a fstab or mtab entry?

the drive, which was prably auto-mounted when you plugged it in, neends to be un-mounted before you can do anything with it in g-parted. the same would apply to the live cd, which also auto-mounts usb drives. you best choice might be the g-parted live cd, the iso for which is available from Sourceforge.

---

### Post by laidback on 2007-08-27
I don't know what is wrong but I can confirm that resize does work with a USB hdd as I have a 250Gb one.
I agree with Duck2006, get a copy of the Gparted Live cd, google for it, it's easy to download and create cd and in my view better than the version that comes with Ubuntu.

Re your current problem, you cannot resize or mess with a partition that's mounted, I reckon that if you've plugged in your usb hdd it will have automounted. Suggest you unmount (umount) it. This can also be done in Gparted, Partition>Unmount.

Hope this helps.

---

### Post by bliffle on 2007-08-27
OK, thanks, guys. It's probably that auto-mount.

I've got the gparted CD as well as rescue CD and I have used them, but I'm darn sure I didn't use them last week for this project.

---

