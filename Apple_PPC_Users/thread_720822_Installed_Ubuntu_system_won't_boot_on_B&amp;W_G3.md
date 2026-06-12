---
title: "Installed Ubuntu system won't boot on B&amp;W G3"
date: 2008-03-10
forum: Apple PPC Users
---

### Post by SeveredCross on 2008-03-10
Okay, so I have a B&W G3 that I bought from a guy. He had put 10.4.6 on it, which was fine, but after fussing around with its damn configuration (I wanted to use it for a filesharing/IRC/etc. server) and not being able to secure the damn thing properly, I figured I might as well install Ubuntu Server on it and get to work on a platform I knew.

I managed to install Ubuntu Server no problem, on a 4 GB hard drive (slaved to the OS X drive).
However, upon reboot, I get the flashing question mark/Finder icon folder, and then boot to OS X.
Nothing I do or say can make it boot to Ubuntu Server. Is this a known issue with the B&W G3? Should I be installing Ubuntu to a master hard drive?

---

### Post by stream303 on 2008-03-10
Have you tried booting by holding down the Alt / Option key to see if you can choose the Ubuntu drive to boot from?

If that fails, it might be possible to boot the server cd in rescue mode, and manually edit your /etc/yaboot.conf and reissue the mkofboot and ybin commands.

I think your other suggestion of installing the server to the master drive would be the easiest solution, and put OSX on the slave drive.  I'd install OSX first on the slave, and then put Ubuntu on the master last, as yaboot will find OSX and include it in the yaboot boot menu.

---

### Post by SeveredCross on 2008-03-11
I'm trying currently to resize the OS X partition to free up 5 GB or so for Ubuntu Server, and seeing if that works. If it does, I'll try to swap them around.

---

