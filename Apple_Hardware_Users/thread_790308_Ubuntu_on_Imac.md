---
title: "Ubuntu on Imac?"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by RedPandaFox on 2008-05-11
Hey, I'm a complete newb when it comes to macs.. But I want to put Ubuntu on an old mac I picked up. Its kind of a running joke with some friends but Id really like to get it working. I don't know the specs of it, but its an old blue Imac running OS 8.5 with all the original software on CD's. The current OS runs well but Id love to get it on Ubuntu or any distro really...
I wasn't sure if this was the right thread so I'm sorry if i posted it to the wrong place. Iv been doing some research but I don't really want to spend 3 Gbs downloading Yellow Dog Linux and I'm not sure if it will even work.
Any suggestions?

---

### Post by stream303 on 2008-05-11
There's quite a few happy PPC iMac owners here, so it can be done.  To find out more about your machine, check this out:
[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

A big factor will be determining how much ram you have.  If you have a small amount of ram, you may want to pursue Xubuntu, or possibly a cli-only install and putting just a touch of xorg, xterm, xdm, etc on top.  In any case, most recommend using the "alternate" ppc installers, rather than the live-desktop images.

Some of the very early iMacs have an 8gb partitioning limitation, which is usually not noticed with original hard drives.  It is when an upgraded hard drive with a larger capacity is installed does this issue surface.  Of course there is a way to make use of the extra space, or one can do an apple firmware update if they have the original mac-os running on a hard drive.

The ATI video card usually needs some tlc along with some manual editing of xorg.conf, and possibly yaboot.conf or passing kernel parameters at the second stage boot: prompt.  Definitely check out these two faqs prior to install:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
and
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

It looks like a lot, but usually a quick edit of one or two config files can get you up and running.

---

