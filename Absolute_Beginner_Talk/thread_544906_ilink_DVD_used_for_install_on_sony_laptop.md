---
title: "ilink DVD used for install on sony laptop"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Teepo on 2007-09-06
Hi Folks;

I have an old Sony SRX87 that I want to make into a music jukebox attached to my home stereo.  I'm having some challenges though, and want to run a couple things by the community while I sort them out.

This laptop has the iLink external DVD drive.  Is it hopeless to do an install from the DVD?  I've fought with Ubuntu failing to find the DVD during installation.  I'm gearing up to do a network install.  I just need to shut down services on my rtr and make my linux desktop a dhcp server, etc for a PXE installation.

---

### Post by tyggna1 on 2007-09-06
If the external drive is USB--then you need to press F12 (or whatever the boot menu option is) and select USB.

It isn't hopeless to install off an external drive.  Heck--if people can install ubuntu off a USB flash driver--then an external DVD wouldn't be too hard.

You may have to press alt-2 at the install from the live CD and type in:

```
mount --bind /dev/sdb /media/cdrom
```
or some other similar function that will mount your USB as a CDROM--but that's not too tough.  Just press alt-F7 when you've got it mounted properly, and the install/boot loader will read it just fine

---

### Post by Teepo on 2007-09-07
Thanks for the reply.  My drive is actualy a Firewire drive branded iLink by sony.  I can boot just fine, but going through alt install, after keyboard is selected, I lose my DVD connection.  The install program is unable to find it.

---

