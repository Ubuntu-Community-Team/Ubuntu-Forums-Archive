---
title: "Debian Wheezy Gnome Shell not working with AMD Radeon"
date: 2012-11-17
forum: Any Other OS
---

### Post by bluedalmatian on 2012-11-17
I have a Lenovo ThinkPad Edge E535 with an AMD RadeonHD graphics chip:

lspci output:

00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9992


The xserver-xorg-video-radeon and xserver-xorg-video-radeonhd packages are installed but Gnome 3 will only start in fallback mode.

Ive installed fglrx-driver and everything that it needs then run aticonfig --initial to generate a new Xorg config file yet I still can only get Gnome 3 to run in fall back mode.

Ive also installed firmware-linux-nonfree.

Im tearing my hair out now. Can anyone help please? Surely someone has got Gnome shell running on this laptop?

Thanks

---

### Post by kiyop on 2012-11-17
Why not asking at debian user forum?
[http://forums.debian.net/](http://forums.debian.net/)

I hope you have read [http://wiki.debian.org/GnomeShell](http://wiki.debian.org/GnomeShell)

---

### Post by JT355 on 2012-11-18
I had  same problem with fallback mode on a desktop. Once day I did an apt-get upgrade and the problem sorted itself out mysteriously. Make sure you are up to date on apt-get upgrade and are using the open source ati drivers, i.e. the xserver-xorg ones.

---

### Post by bluedalmatian on 2012-11-18
> **kiyop said:**
> Why not asking at debian user forum?
[http://forums.debian.net/](http://forums.debian.net/)

I hope you have read [http://wiki.debian.org/GnomeShell](http://wiki.debian.org/GnomeShell)

Ive asked on the Debian user mailing list but no one replied

---

