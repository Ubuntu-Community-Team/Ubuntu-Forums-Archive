---
title: "Making a live Ubuntu usb drive stick"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by bd1886 on 2007-01-06
First time here! New to Linux and decided to use Ubuntu. Have a live cd and absolutely dug the whole package. I'm also new to computing... (trial by fire I guess) so pretty much of a clean slate. Would like to have this distro on a usb drive format. Is this possible. How much hd space does it take up on a drive w/o extensions? Thanks for any help.

---

### Post by MkfIbK7a on 2007-01-06
ubutntu takes up 4gb minimum

but i would suggest xubuntu for a usb stick only 1.4gb minimum

---

### Post by garak on 2007-01-13
> **wert613 said:**
> ubutntu takes up 4gb minimum

but i would suggest xubuntu for a usb stick only 1.4gb minimum

4gb? So how the live CD could stay on about 600mb? :-k

---

### Post by Frank Golden on 2007-01-13
> **bd1886 said:**
> First time here! New to Linux and decided to use Ubuntu. Have a live cd and absolutely dug the whole package. I'm also new to computing... (trial by fire I guess) so pretty much of a clean slate. Would like to have this distro on a usb drive format. Is this possible. How much hd space does it take up on a drive w/o extensions? Thanks for any help.

See here for info on how to make a persistent Live USB stick.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29)

You must be able to boot to your USB disk in BIOS.
Using this tutorial I have Ubuntu 6.06 LTS on a 2GB Cruzer Titanium.
Boots much faster, runs faster and some changes are persistent. Like bookmarks and home pages in Firefox. Real slick.

BTW, My Ubuntu installs (Dapper and Edgy) start out around 2 to 2.5GB. After customizing and adding programs and such, I end up with something like 3.75GB.
So allocating 4Gb for an Ubuntu install is the bare minimum, IMHO.

I too am puzzled how they manage to get compleat Ubuntu on a 600MB CD.

---

### Post by jvc26 on 2007-01-13
The ubuntu on the CD has the OS and the base apps on it (from the ubuntu-desktop metapackage) Theyre all compressed - note when you download an app from apt-get and you get the return on how big the download is, its often a lot smaller than the installed space. Therefore with a smaller number of apps (as you get the extra ones you want when you first open up) and compression thats my guess on the way it fits on a CD.
Il

---

### Post by bd1886 on 2007-01-15
These types of possibilities scream why Linux is the way!! Wish there was a boot camp!!.

---

