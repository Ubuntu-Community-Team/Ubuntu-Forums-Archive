---
title: "IS there any way to move a ubuntu installation to another computer?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-13
IS there any way to move a ubuntu installation to another computer?
I have fully configured ubuntu in my desktop computer and now i want the same set of applications and configuration in my laptop, is there any way to migrate the configuration and applications to another computer?

Thanks.

---

### Post by voteforpedro36 on 2008-01-13
Well, you could make a CD of your current OS (it's possible... I don't know the name of the tool, sorry). But you can't just copy everything over. That would cause problems.

---

### Post by dstew on 2008-01-13
I think this is only possible if the other system has *exactly* the same hardware (same motherboard, disks, video etc.) This is because your Ubuntu installation is tailored to your hardware. That what the installation disk does. It detects your hardware, and installs the appropriate kernel modules.

The best you can do is save your Home directory, and copy it into a new Ubuntu installation.

---

### Post by edm1 on 2008-01-13
not really because the system is configured to your specific hardware. you could backup your entire home folder then move it onto your new system in order to preserve all your configuration files, then it would only be a matter of reinstalling the applications.

---

### Post by asmoore82 on 2008-01-13
clonezilla ... [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

you would need to download and burn their Clonezilla Live CD...
you boot from it and you can do perfect clones ...
 *to/from images on portable drives
 *to/from drives in the same PC
 *to/from drives in different PCs over network

Clonezilla is a smart imaging tool that only sends the data it has to,
the "used" blocks of a partition, so it's also superfast compared to
others such as Super UDPcast. However, Super UDPcast is much
easier for a first time user... [http://udpcast.linux.lu/bootmedia.html](http://udpcast.linux.lu/bootmedia.html)

---

### Post by asmoore82 on 2008-01-13
The hardware must be exactly the same *for a Windows clone* to be successful.
However, Linux is, once again, proven **much better**.

I cloned from my old laptop to my new one with Clonezilla with no problems,
you can get away with pretty much anything in cloning Linux as long as you
use common sense... My old laptop had ATI graphics but the new one doesn't;
so, naturally, I reconfigured Xorg from the console before trying to do a full
boot into the new system.

Xorg driver and "Restricted" Drivers would be the only things to watch out for that
may cause problems. The proper "Drivers" (kernel modules) for everything else are
loaded automagically "on-the-fly" at boot time by the kernel.

Oh, and one more ***SUPER IMPORTANT*** thing. For UDPcast *it doesn't matter*,
but for clonezilla you *may* have to edit "/etc/fstab" and set everything to mount
by device and not by UUID;
which sounds really complicated but is actually just some cutting and pasting.

---

### Post by legolas_w on 2008-01-16
Thank you.
Can you please let me know whether the clonezilla will clone my ntfs partition which are mounted in my linux?

I have all my NTFS partition available in Ubuntu 7.10 and I dont want them to be cloned, I just want to save linux and all softwares that I installed so far.


Thanks.

---

### Post by kpkeerthi on 2008-01-16
You can. I have successfully copied a tar of my laptop's / partition to my desktop. I had to reconfigure 'X' and make changes to /etc/fstab according to partition layout of my desktop. Linux makes it incredibly easy to clone across varying hardwares.

---

