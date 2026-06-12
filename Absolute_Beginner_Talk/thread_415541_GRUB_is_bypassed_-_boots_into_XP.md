---
title: "GRUB is bypassed - boots into XP"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by SegaBoy0 on 2007-04-20
Hey everyone, **first** post here...love these forums as they've helped me with my first linux install of 7.04 last night.  Everything is working great...except for the following:

I had a previous install of XP on one hard drive.  Then installed Ubuntu 7.04 on a separate clean hard drive.  After the successful install, GRUB is now getting bypassed and Windows XP is booted automatically every time I start up.  I can workaround this by booting from the 7.04 Live CD, then choosing to boot from hard disk.  But that's kind of a hassle.

Is there a way I can edit menu.1st so GRUB pops up before Windows is booted?  Thanks. :)

---

### Post by LaRoza on 2007-04-20
You are using two different hard drives?

I am not exactly sure, but it seems like MBR is located on your first hard drive with Windows and GRUB is on the other.

---

### Post by LordFu on 2007-04-20
Make the drive with GRUB your master drive. Boot once without the XP drive attached. Hook up the xp drive as the slave. You should get the GRUB menu on boot from then on.

---

### Post by SegaBoy0 on 2007-04-20
> **LaRoza said:**
> You are using two different hard drives?

Yep, 2 different HDs.  That could very well be the case that MBR is on the windows drive and GRUB on the other.  Does anyone know if WinGRUB is worth using?  I'm sure this would fix my problem but not sure if I want to go that route.

---

### Post by SegaBoy0 on 2007-04-20
> **LordFu said:**
> Make the drive with GRUB your master drive. Boot once without the XP drive attached. Hook up the xp drive as the slave. You should get the GRUB menu on boot from then on.

That should probably do it...thanks guys.

---

### Post by lluisanunez on 2007-04-20
Yes GRUB should be on the other disk

You'll need to chroot into your ubuntu installation, either from the install cd or another live cd.

```
mount /path/to/rootpartition /path/to/mountpoint
chroot /path/to/mountpoint /bin/bash

```

Now you've chrooted into your installation. Time to install grub

```
grub-install -root-directory Mount-Point (hdn) 
```

Installs grub into the MBR of a hard disc. The option gives the path to the kernel-image, if it is not in /, f.e. in /boot.
(hdn) is a disc, where n is the number of the disc, starting with 0.

Now edit /boot/grub/menu.lst for including all operating systems you want to load. Probably there is already an entry for ubuntu

---

### Post by oilchangeguy on 2007-04-20
follow the advice in post #3. that's how i've got my dual boot, 2 hard drives set up and it works with no problems.

---

