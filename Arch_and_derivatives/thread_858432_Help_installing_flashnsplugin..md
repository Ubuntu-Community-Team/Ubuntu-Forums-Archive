---
title: "Help installing flash/nsplugin."
date: 2008-07-13
forum: Arch and derivatives
---

### Post by paulie1984 on 2008-07-13
Hi, Im having some trouble installing flash and nsplugin. Here is what I did so far.

```
pacman -Sy --asdeps gtk2 lib32-atk lib32-cairo lib32-expat lib32-fontconfig lib32-freetype2 lib32-gcc-libs \
  lib32-glib2 lib32-glibc lib32-gtk2 lib32-libice lib32-libpng lib32-libsm lib32-libx11 lib32-libxau \
  lib32-libxcb lib32-libxcursor lib32-libxext lib32-libxfixes lib32-libxft lib32-libxi lib32-libxinerama \
  lib32-libxmu lib32-libxrandr lib32-libxrender lib32-libxt lib32-pango lib32-pcre lib32-zlib libxt \
  util-linux-ng lib32-alsa-lib lib32-libxdamage lib32-libstdc++5 rpmextract

```

```
I also downloaded both of these tarballz
nspluginwrapper
http://aur.archlinux.org/packages.php?do_Details=1&ID=6217&O=0&L=0&C=0&K=nspluginwrapper&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd
nspluginwrapper-flash
http://aur.archlinux.org/packages.php?do_Details=1&ID=6232&O=0&L=0&C=0&K=nspluginwrapper&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd


```

I have the tarballz on my desktop, but now what? when I enter makepkg --asroot It tells me there is no Package. How and where do I extract the tars? and after that what do I do? the arch beginners guide is what im reading, but it's doesnt give enough information on what to do in this area. I just want flash to work lol.

Here is a SS:
[[img]http://xs229.xs.to/xs229/08291/screenshotom9112.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs229&d=08291&f=screenshotom9112.png)

---

### Post by Rumor on 2008-07-13
From the AUR page, dowbload the PKGBUILD file to your download directory. From a terminal cd to that directory and then run makepkg

Makepkg should read the PKGBUILD file, go out and download the source and build the package for you.

Here's a bit more reading for you:

[http://wiki.archlinux.org/index.php/AUR_User_Guidelines#Using_Packages_from_UNSUPPORTED](http://wiki.archlinux.org/index.php/AUR_User_Guidelines#Using_Packages_from_UNSUPPORTED)

[http://wiki.archlinux.org/index.php/AUR](http://wiki.archlinux.org/index.php/AUR)

[http://wiki.archlinux.org/index.php/Makepkg](http://wiki.archlinux.org/index.php/Makepkg)

---

### Post by crimesaucer on 2008-07-16
I'm sure you already have this wiki page: [http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64](http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64)


... but to explain this a bit (you should read those 3 wiki pages that Rumor linked you to), I'll add some info on a part that's a little confusing.


so after installing those dependencies, and downloading both of those AUR tarballs to your desktop, what you need to do is unpack both tarballs to create a the nspluginwrapper and nspluginwrapper-flash folders on your desktop, then go into the nspluginwrapper folder and in a regualr terminal, run:

```
makepkg -s
```

then in a Root terminal, upload the pkg with:

```
pacman -U nspluginwrapper-*.tar.gz
```


...after that log out of Root and back into a regular terminal, you can now go into your nspluginwrapper-flash folder and run this again:

```
makepkg -s
```

and then this from a Root terminal again:

```
pacman -U nspluginwrapper-flash-*.tar.gz
```

now, log OUT of root, back into a regualr terminal, and create a plugin directory in your ~/.mozilla if you don't have one...

```
mkdir ~/.mozilla/plugins
```

and then (still in a a regualr user terminal) run this:

```
nspluginwrapper -v -a -i
```


...don't mind any errors from plugins like mozplugger or totem... this is all from that wiki page, and it worked for me.

---

