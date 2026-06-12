---
title: "Refresh USB devices"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by frederick1978 on 2007-09-17
[I]Dear all,

Sometimes when I plug a USB storage peripherical or even a USB device, the operative system doesn't recognize it.
It is enough to restart Ubuntu to have everything working again.
Is it possible to re-initialize manually the devices from the command line.

Thanks 

          Regards[/I]

---

### Post by bone2006 on 2007-09-18
Have you tried unmounting and remounting the device?  If it doesn't show it mounted at all, then I would imagine it wouldn't even be a problem unplugging it and plugging it back in

---

### Post by jaygo on 2007-10-31
I'm wondering the same thing as the OP. When I swap out SATA drives, the drive disappears from fdisk -l and I don't know how to make the system redetect devices without rebooting. Anyone have a console or GUI method?

---

### Post by OliW on 2008-01-02
UltraBump!

I'm determined not to restart each and every time I need to plug in a new drive. I'm using my windows box as a USB conduit at the moment and I'm not liking a second of it.

Just to clarify, sometmies when I plug a memory stick or a camera in, nothing happens. Usually it auto-mounts or it shows up in computer:///.

lsusb does show the device, it just doesn't seem to get any further than that.

---

### Post by JRue on 2008-05-21
Same issue here. Did anyone have a non-reboot fix?

---

### Post by ndo on 2008-05-30
Why does no one in the community help answer questions regarding USB mount issues?

Do they not believe it is happening? Or does nobody know of a solution for these problems?

My usb (which work fine - still - when I boot into windows) not only won't allow me to swap devices, the connectivity shuts off entirely after about 10 minutes after boot up. This is very frustrating, and no one has even tried to offer a solution. Lack of BASIC usb functionality is a definite deal breaker with Ubuntu, and has almost driven me back to windows. 

Some help from you Linux/Ubuntu old school pimps would be really appreciated about now...

---

### Post by OliW on 2008-05-30
I did have a bit of a fix. It turns out that sometimes this was caused by a crashing application. Once I figured out which process it was and killed it, the USB functions became responsive again. YMMV.

---

