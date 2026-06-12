---
title: "deleting media/usbdisk"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by jubilee0824 on 2007-06-19
Hi

I started using Ubuntu few weeks ago, and now updated to 7.0.4.
I just realized that i got a small but annoying problem.

My usb drive and external drive, which were used to be mounted on /media/usbdisk and /media/SVault, are now mounted as /media/usbdisk_ and /media/SVault_
I figured out that this happens because there are already empty folders named /media/usbdisk and /media/Svault even when these drives are not mounted. And when Ubuntu tries to mount, it creates new folders with "_" at the end. So I tried to remove /media/usbdisk and /media/SVault, hoping that drives will be mounted without "_" again.

I tried, rm -f and rmdir but not succeeded so far. This is giving me a little headache because most software still refers to /media/Svault as my external drive and keep failing to find files in it! Can anyone suggest a solution please?

---

### Post by benanzo on 2007-06-19
Make sure that nothing is mounted into those folders:
```

sudo umount /media/usbdisk
sudo umount /media/Svault

```
(I would disconnect the USB drives just in case)
Then do:
```

sudo rm -rf /media/usbdisk
sudo rm -rf /media/Svault

```

Then plug your drives back in.  I don't know why that wouldn't fix it.

---

### Post by jubilee0824 on 2007-06-19
Thanks...I totally forgot this powerful command, rm -rf.
I will try that after getting back from my work.
Cheers.

---

### Post by jubilee0824 on 2007-06-20
and it (of course) worked without a problem! thanks!

---

