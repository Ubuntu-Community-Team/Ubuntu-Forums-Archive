---
title: "Won't install on g3 ibook"
date: 2009-06-13
forum: Apple Hardware Users
---

### Post by Whamola on 2009-06-13
So I've been trying to install Ubuntu on my ibook (6.10 and/or 7.04) and holding C and I sit at the grey screen for a couple minutes, then osx 10.3.9 boots as normal.  Holding down alt to get to get to the hard drive/cd selection screen I get the choice of wither, but when I click on the Linux icon, the colors on the screen distort and it stays on this menu.  
Also, I am running the cd on a external usb (1.1 built in to ibook) cd drive due to the internal drive being dead.
I guess what I'm asking is:  Is there any way to get this to boot from the cd or any other way?

Thanks in advance

---

### Post by PhirePhly on 2009-06-13
I've had success netboot installing on my G3, though like everything else, it's broken out of the box.  I'm making a lot of assumptions on how proficient you are, along with you having another *nix computer available, so if this is way out of your range, I apologize.

All of my notebooks are packed right now for moving this weekend, so I can't find you the dhcp conf stuff right now, but I know that you need to setup a tftp server on another machine, and setup a dhcp server to give your ibook a static ip address and to boot from the file /yaboot . If you can't figure out how to do that, I can find it for you Monday.

You need to download some files to put in /var/lib/tftpboot for your ibook to boot off of.  From: [http://ports.ubuntu.com/dists/jaunty/main/installer-powerpc/current/images/powerpc/netboot/](http://ports.ubuntu.com/dists/jaunty/main/installer-powerpc/current/images/powerpc/netboot/)
You need: boot.msg initrd.gz vmlinux yaboot.conf

Normally, you would also download yaboot, but it's broken, so you need to download the patched version I built:
[https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/26426/comments/18](https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/26426/comments/18)

Then connect your ibook to the network and tell it to boot off the network (assuming that model is able to do that?).  Either press n, or I prefer to open openfirmware (alt-apple-o-f) and type 
```
boot enet:0
```

It will download yaboot, display boot.msg, press return and it'll start installing (hopefully).  I'm not checking to make sure this is all even possible, so take my advice with a grain of salt.

---

### Post by MikeTheC on 2009-06-14
Not going to work. You can't boot that system via USB. Sorry.

If you've got a FireWire port on it, you could try to find and buy a FireWire optical drive instead, and that would work.

---

### Post by tgalati4 on 2009-06-14
Some older ibook drives only read 650 mb cd's.  Those disks are hard to find.

True, only firewire external boot is supported.

---

