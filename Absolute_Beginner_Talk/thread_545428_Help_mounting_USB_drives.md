---
title: "Help mounting USB drives"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by praneeth on 2007-09-07
Hi,

I have installed edubuntu server and configured the thin clients successfully and working fine..

When i connect the USB Device on my thin clients and server the drive do not mount and also it do not recognize the device.


how can i fix this problem..

Thanks,
Praneeth.

---

### Post by dwhitney67 on 2007-09-07
Does your kernel provide USB support?  Let's assume that it does... are the proper drivers built into the kernel or are they available as modules?

If they are built in, then this command might work for you if you want to mount the mem-stick manually:

[FONT="Courier New"]$ sudo mkdir -p /media/usb
$ sudo mount -t vfat /dev/sda1 /media/usb[/FONT]

Of course, the /dev/sda1 is only a guess.  Your USB stick might reside on a different device (for example, /dev/sda2, /dev/sda3, etc).

If the USB drivers are not built into the kernel, then you will have to load them manually (or you can specify that these are loaded during system startup).  I forgot exactly what the module names are (it may be *usbcore*), but they are loaded using the 'modprobe' command.  For example,

[FONT="Courier New"]$ sudo modprobe <kernel module>[/FONT]

If you run this command and immediately return to the command line prompt, then the driver was loaded successfully; if it fails you will know that from the error message that is spewed out.

Once the driver is loaded, then you can proceed to mount the USB mem-stick using the commands given earlier.

This may all sound like an inconvenience.  This is where the HAL daemon comes into play.  It can be used to auto-mount your USB devices (if the proper "rules" are available) automatically.  However since you are running a server I am not sure if you have the HAL daemon running.  If you do have it running, and your USB mem-stick is not auto-mounting, then it is probably something to do with the HAL "rules".  Do a Google search for more information on HAL.  I for one am no expert on the subject.

---

