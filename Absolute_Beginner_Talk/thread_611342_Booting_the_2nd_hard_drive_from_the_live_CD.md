---
title: "Booting the 2nd hard drive from the live CD?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Orangutan on 2007-11-12
Hi all,

I have installed ubuntu on my second sata drive, sdb, I did not install the boot loader, I would like to boot off the live CD, but I do not know the boot options to do this.

Is there any way to boot the second hard drive without installing the boot loader, I do not want to make any changes to the primary hard drive, as that has my visit the installation on it at the moment.

Thanks in advance.

---

### Post by Iceni on 2007-11-12
I belive you can simply go into the bios and select this hard drive as your first boot device.

---

### Post by Orangutan on 2007-11-12
Thanks, I tried to just boot that hard drive but the computer hangs, So i figure I have to re-install from scratch and install a boot loader on that device too.

In the advanced options, I tried "/dev/SCSI4" as the device to put the boot loader on, all good until there is a fatal error at the end of the instalation when it tries to do that,

So now I'm trying again with /dev/sdb as the target for the boot loader, it's installing now, I'll update when it's done, if it works.

What I'd Ideally like to do is to be able to boot my machine from a usb memory stick, sort of like a Ubuntu "key" for my machine, does anybody have a pointer for a newbie like me to be able to do that?

Oh.. update it looks like /dev/sdb woked, im going to restart now...
Wish me luck.
;)

---

### Post by Orangutan on 2007-11-12
Update,

That worked, although it was a bit of a pain having to install 3 times. ;)

Oh and I had to change root (hd1,0)
to
root (hd0,0) to get it to boot. 

Hope this info helps someone else, and thanks for the pointers.
O
:)

---

