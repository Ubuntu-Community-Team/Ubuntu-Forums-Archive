---
title: "Little help needed with freebsd"
date: 2011-11-09
forum: Any Other OS
---

### Post by Legend_Xeon on 2011-11-09
Hi there,
After spending sometime with ubuntu, i want to install freebsd in conjunction with ubuntu(dual boot).
Now i have this freebsd download link:- [http://torrents.freebsd.org:8080/](http://torrents.freebsd.org:8080/) and the following are the list of files from which i have to choose relevant file for my system,
[FreeBSD-8.2-RELEASE-i386-bootonly]("http://torrents.freebsd.org:8080/stats.html?info_hash=e86c8124f8c942a3b3bff101b97d908bf26c5b73")           (46.98 MB)
[FreeBSD-8.2-RELEASE-i386-disc1]("http://torrents.freebsd.org:8080/stats.html?info_hash=b67f1627d0b0993301c3d152f7433318283c989e")                (653.25 MB)
[FreeBSD-8.2-RELEASE-i386-dvd1]("http://torrents.freebsd.org:8080/stats.html?info_hash=1b1788095a4ffd4d9d7bed46a89089c2cda36d5d")                (2.12 GB)
[FreeBSD-8.2-RELEASE-i386-livefs]("http://torrents.freebsd.org:8080/stats.html?info_hash=432c6b989db7ee92624e1199f53bec15a3108c49")                (252.16 MB)
[FreeBSD-8.2-RELEASE-i386-memstick]("http://torrents.freebsd.org:8080/stats.html?info_hash=caf0f3943cc9c244e9bf034ef2b27a5edc117827")         (914.20 MB)

From these i have to choose only dvd1(2.12 GB). Right?
Also what are the other files for?

---

### Post by lisati on 2011-11-09
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by mips on 2011-11-09
[http://www.freebsd.org/releases/8.2R/announce.html](http://www.freebsd.org/releases/8.2R/announce.html)
> [B]Availability
[/B]
FreeBSD 8.2-RELEASE is now available for the amd64, i386, ia64, pc98, powerpc, and sparc64 architectures.

FreeBSD 8.2 can be installed from bootable ISO images or over the network. Some architectures (currently amd64 and i386) also support installing from a USB memory stick. The required files can be downloaded via FTP or BitTorrent as described in the sections below. While some of the smaller FTP mirrors may not carry all architectures, they will all generally contain the more common ones such as amd64 and i386.

MD5 and SHA256 hashes for the release ISO images are included at the bottom of this message.

The purpose of the images provided as part of the release are as follows:

dvd1
This contains everything necessary to install the base FreeBSD operating system, a collection of pre-built packages, and the documentation. It also supports booting into a "livefs" based rescue mode. This should be all you need if you can burn and use DVD-sized media.

disc1
This contains the base FreeBSD operating system and the documentation packages for CDROM-sized media. There are no other packages.

livefs
This contains support for booting into a "livefs" based rescue mode but does not support doing an install from the CD itself. It is meant to help rescue an existing system but could be used to do a network based install if necessary.

bootonly
This supports booting a machine using the CDROM drive but does not contain the support for installing FreeBSD from the CD itself. You would need to perform a network based install (e.g. from an FTP server) after booting from the CD.

memstick
This can be written to an USB memory stick (flash drive) and used to do an install on machines capable of booting off USB drives. It also supports booting into a "livefs" based rescue mode. The documentation packages are provided but no other packages.

As one example of how to use the memstick image, assuming the USB drive appears as /dev/da0 on your machine something like this should work:

# dd if=FreeBSD-8.2-RELEASE-amd64-memstick.img of=/dev/da0 bs=10240 conv=sync
Be careful to make sure you get the target (of=) correct.

FreeBSD 8.2-RELEASE can also be purchased on CD-ROM or DVD from several vendors. One of the vendors that will be offering FreeBSD 8.2-based products is:

FreeBSD Mall, Inc. [http://www.freebsdmall.com/](http://www.freebsdmall.com/)

If you have not used FB before or unsure maybe just stick with the DVD

---

### Post by jackdale on 2011-11-09
I recommend the DVD as it gets you going quicker than the cd (given the extra packages) - unless you have download limits or slow connection and only want to download the necessary packages.

Also, depending on what you want to do with it, FreeBSD 9.0 should be released in the next month or so (I hope).  The RC1 was released a little over a week late.  We should have had the RC3 out by now, but RC1 had a few more bugs than expected.   This will be quite a big improvement from 8.x, but they want to make sure it is solid before release.

Also, if you haven't used FreeBSD before, be aware that it will install only the CLI;   FreeBSD does not come with a GUI or even xorg.  If you want FreeBSD to install with a GUI, the best option (IMHO) is [PC-BSD]("http://www.pcbsd.org/")  It is built on FreeBSD and closely follows the FreeBSD release schedule and many consider it to be the Ubuntu of the BSDs.  It comes with KDE desktop, but you can also have Gnome2 on it (you'd have to install it yourself though).  Gnome 3 has not yet been ported.

Either way, FreeBSD is a fantastic and solid OS.  I would not hesitate to recommend it as a server.  PC-BSD is a really good desktop OS.  In many ways it makes Linux distros look like the poor cousins (in terms of under-the-hood stuff).  However, it does not have the software availability that Ubuntu has (although it now comes with a great package management software-center-like app) and many more apps are being ported than ever before.  It is also missing support for some proprietary hardware and cannot play some common media formats.

Still, apart from these, Ubuntu users would should feel at home when using PC-BSD.

---

### Post by Legend_Xeon on 2011-11-10
Thanks jackdale and mips.
I got the DVD and installed it and got it working without any problems on one of my systems.

---

