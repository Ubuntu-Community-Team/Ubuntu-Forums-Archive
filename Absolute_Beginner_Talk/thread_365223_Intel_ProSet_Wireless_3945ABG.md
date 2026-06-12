---
title: "Intel ProSet Wireless 3945ABG"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by TheNewbie on 2007-02-19
hello,
 I have installed Ubuntu onto my PC, but found my wireless is not working. So I went back to XP and found there's a driver for it. My question is this:

**if I save the driver onto a CD, can I insert it into Ubuntu and install it from there? **

In XP you can do things like that.... I am just wondering if it works in Ubuntu....


Help,
Jess

---

### Post by TheNewbie on 2007-02-19
Anyone? :(

---

### Post by mikewhatever on 2007-02-19
Not sure about the driver thing, but that wireless card should work. You may need to install linux restricted modules for your kernel either from synaptic (search for linux restricted), if you have wired connection, or download the package from:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all)

make sure to install the right modules for your kernel
> uname -a to check which kernel you have

---

### Post by mikewhatever on 2007-02-19
By the way, before you install, how do you know the wireless isn't working?

---

### Post by getaceres on 2007-02-19
I have that card and it works out of the box. Just install network-manager-gnome and enjoy.

---

### Post by TheNewbie on 2007-02-19
I know it isn't working because I installed Ubuntu onto my 2nd harddrive. It didnt work. Oh and getaceres, how can you install network-manager-gnome if you dont have a working internet connection?

---

### Post by mikewhatever on 2007-02-19
Have you tried checking in System->Administration->Networking? Is there a wireless connection?

---

### Post by getaceres on 2007-02-19
Apart from mikewhatever's response, you can install it if you have the install cds, not the live cds (for whatever reason is not included in the default cd and you need to download the alternate one).

---

### Post by annda on 2007-02-19
> **TheNewbie said:**
> how can you install network-manager-gnome if you dont have a working internet connection?

you can download the .deb package from packages.ubuntu.com under another OS (and all the packages it depends on - listed on the site) and save them somewhere or burn them to a cd.

then you can install them by double-clicking (tricky because of dependencies), or add the cd to software sources in synaptic.

---

