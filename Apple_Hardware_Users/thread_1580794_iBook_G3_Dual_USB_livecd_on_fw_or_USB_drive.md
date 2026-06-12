---
title: "iBook G3 Dual USB livecd on fw or USB drive?"
date: 2010-09-23
forum: Apple Hardware Users
---

### Post by plumper on 2010-09-23
I have an old iBook G3 12" Dual USB (M7692LL/A) with 128Mb extra of RAM.

I was trying to boot Ubuntu from an external USB DVD and a FW CD drive, and the same thing happened.  When I select the disc from the boot select screen and press enter, the colors get funky and it stays like that for minutes!

HELP!!  :confused:

---

### Post by linuxopjemac on 2010-09-24
Don't even try liveCD's. Install from alternate or netboot immediately and change xorg.conf later:

wget [http://mac.linux.be/files/xorg/ibook1.txt](http://mac.linux.be/files/xorg/ibook1.txt)
```
sudo mv ibook1.txt /etc/X11/xorg.conf
```

alternate: [http://cdimage.ubuntu.com/ports/rele...te-powerpc.iso](http://cdimage.ubuntu.com/ports/rele...te-powerpc.iso)

netboot: [http://ports.ubuntu.com/ubuntu-ports...tboot/mini.iso](http://ports.ubuntu.com/ubuntu-ports...tboot/mini.iso)

---

### Post by plumper on 2010-09-24
I'll let you know how it goes.  Just in case, how do you netboot it?    :confused:

---

### Post by linuxopjemac on 2010-09-25
Here I booted a Debian netinstall, it's the same for Ubuntu:
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

---

### Post by plumper on 2010-09-25
Thank you SOOO much!!  I'm booting it off of an ext USB DVD-ROM using the alt install cd!

All I needed was the Open Firmware help from your blog!  You're awesome!

:guitar:

---

