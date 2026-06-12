---
title: "apmd help"
date: 2009-01-20
forum: Arch and derivatives
---

### Post by kerry_s on 2009-01-20
is there a special repo for apmd?
can anyone tell me how to install it in arch?

thanks.

---

### Post by cdtech on 2009-01-20
Have you installed:
```
sudo apt-get install apmd
```
Or try:
```
apmd -V
```
To issue a command using the ampd, it should be the application followed by a command flag. See "man apmd".........

---

### Post by mips on 2009-01-20
[http://aur.archlinux.org/packages.php?O=0&L=0&C=0&K=apmd&SeB=nd&SB=n&SO=a&PP=25&do_Search=Go](http://aur.archlinux.org/packages.php?O=0&L=0&C=0&K=apmd&SeB=nd&SB=n&SO=a&PP=25&do_Search=Go)

You can install it with Yaourt, [http://archlinux.fr/yaourt-en](http://archlinux.fr/yaourt-en)

```
yaourt -S apmd
```

---

### Post by cdtech on 2009-01-20
My bad. I missed the arch...I gotta go sleep now...:)

---

### Post by kerry_s on 2009-01-20
> **mips said:**
> [http://aur.archlinux.org/packages.php?O=0&L=0&C=0&K=apmd&SeB=nd&SB=n&SO=a&PP=25&do_Search=Go](http://aur.archlinux.org/packages.php?O=0&L=0&C=0&K=apmd&SeB=nd&SB=n&SO=a&PP=25&do_Search=Go)

You can install it with Yaourt, [http://archlinux.fr/yaourt-en](http://archlinux.fr/yaourt-en)

```
yaourt -S apmd
```


thanks, but that package is a bad link.
i've been there before and tried.

---

### Post by kerry_s on 2009-01-20
> **cdtech said:**
> My bad. I missed the arch...I gotta go sleep now...:)

if only it were that easy, i just dumped debian for arch, cause they keep dropping my firmware from the old systems.

no problem, get some rest. :)
i know how you feel i did that post before going to work this mourning and just now got home, damn 10 hour days. :mad:

---

### Post by kerry_s on 2009-01-20
hey guys, i'm going to go ahead and close this out, i just found out it was deleted from extra by the arch developers cause they felt apm/apmd is not used any more for i686 computers, i guess none of them own a old thinkpad. in any case i'll just have to find another way to get the functions i need.

---

### Post by fwojciec on 2009-01-20
It seems to be still available from AUR: [http://aur.archlinux.org/packages.php?ID=20861]("http://aur.archlinux.org/packages.php?ID=20861")

---

### Post by kerry_s on 2009-01-21
> **fwojciec said:**
> It seems to be still available from AUR: [http://aur.archlinux.org/packages.php?ID=20861]("http://aur.archlinux.org/packages.php?ID=20861")

dude, click those links see what you get.

---

### Post by fwojciec on 2009-01-21
AUR page for apmd package.  Wasn't that what you were looking for?

---

### Post by smartboyathome on 2009-01-21
> **fwojciec said:**
> AUR page for apmd package.  Wasn't that what you were looking for?

I get the same thing. Try clearing your cache if you don't, then try again.

---

### Post by kerry_s on 2009-01-21
click the link to download it, it's not there.

it's alright guy's i'll roll with it, i'm already thinking about going back to debian. as long as apm is in the kernel they should provide the tools to use it. but that's fine it's there call. i'm not picky and will go with the distro that works 100%, i don't have a burner right now so i'm just using what i got.

---

### Post by fwojciec on 2009-01-21
To install a package from AUR you have to get the tarball from AUR page, extract it, change to the directory with the PKGBUILD file and run makepkg command, probably with -s switch so that it downloads dependencies automatically.  This will create a package file *.pkg.tar.gz that can be installed with pacman -U command.

There is more info about ABS/AUR/makepkg in the wiki, if you decide to stay with Arch -- these are absolutely essential tools, without them Arch is just another distro.

---

### Post by kerry_s on 2009-01-21
> **fwojciec said:**
> To install a package from AUR you have to get the tarball from AUR page, extract it, change to the directory with the PKGBUILD file and run makepkg command, probably with -s switch so that it downloads dependencies automatically.  This will create a package file *.pkg.tar.gz that can be installed with pacman -U command.

There is more info about ABS/AUR/makepkg in the wiki, if you decide to stay with Arch -- these are absolutely essential tools, without them Arch is just another distro.

okay, i got it, stupid me i been clicking where it says "Source" daaa. 10 hour work day will make you blind to the obvious.

so anyway i got the apmd.tar.gz, let me hit up the wiki and i'll get back with the results.

hey, i want to thank you guys for sticking with me, i really am trying to get use to arch, i really do appreciate the help.

---

### Post by kerry_s on 2009-01-21
i keep getting failed. :(

---

### Post by fwojciec on 2009-01-21
It looks like the website that used to host the sources is no more.  I know what you mean about clicking on links now :)

Anyways, I made a PKGBUILD based on the source file used for Ubuntu Jaunty -- it's also a more recent version of the package.  Just replace the PKGBUILD in the extracted directory with this (it needs to be in the same directory because the build script still needs one of the files that come in the tarball from AUR).

```
# $Id: PKGBUILD 2304 2008-05-31 05:00:40Z paul $
# Maintainer: dorphell <dorphell@archlinux.org>
pkgname=apmd
pkgver=3.2.2
pkgrel=1
pkgdesc="Set of tools for managing notebook power consumption"
depends=('glibc')
makedepends=('libxaw')
backup=('etc/apmd_proxy')
arch=(i686 x86_64)
license=('GPL2')
url="http://www.worldvisions.ca/~apenwarr/apmd/"
source=(https://launchpadlibrarian.net/19723200/apmd_3.2.2.orig.tar.gz apmd.rc)
md5sums=('b1e6309e8331e0f4e6efd311c2d97fa8'
         'e84ca8f326aeb5b982c1f6585b183d70')

build() {
  cd $startdir/src/$pkgname*
  #patch -Np1 -i ../apmd-$pkgver.patch
  make || return 1
  mkdir -p $startdir/pkg/{usr,etc}
  make PREFIX=$startdir/pkg/usr APMD_PROXY_DIR=$startdir/pkg/etc install
  install -D -m755 ../apmd.rc $startdir/pkg/etc/rc.d/apmd
  rm -rf $startdir/pkg/usr/man/fr
}
```

No guarantees -- but it should work.  I was able to build it on my machine, but I have no means of testing it further.

---

### Post by kerry_s on 2009-01-21
you are the man! 
it just had a file conflict, so i had to rename a file. anyways 
it worked got it installed, now i just got to figure out how to use it. i need it to restore sound and network after resume from suspend.

---

### Post by SomeGuyDude on 2009-01-21
> **kerry_s said:**
> okay, i got it, stupid me i been clicking where it says "Source" daaa. 10 hour work day will make you blind to the obvious.

so anyway i got the apmd.tar.gz, let me hit up the wiki and i'll get back with the results.

hey, i want to thank you guys for sticking with me, i really am trying to get use to arch, i really do appreciate the help.

Tip: install Yaourt and then everything in the AUR you can install with "yaourt -S [package]". Don't even need to run it as root. :D

---

### Post by mips on 2009-01-21
> **SomeGuyDude said:**
> Tip: install Yaourt and then everything in the AUR you can install with "yaourt -S [package]". Don't even need to run it as root. :D

+1

Yaourt is usually the first thing I install on a fresh Arch install. Also have a look at Powerpill.

---

### Post by kerry_s on 2009-01-21
well guys, i've decided just to stick with the standard repos. i boned that other install, so i'm in the process of installing a fresh install now.
i'm just planning on using just the standby(fn+f3) which should be good enough. i need the system ready by friday for my niece, so i'm not going to bother messing with it for now, just get it back up and running, she only needs firefox and flash, yeah she's a youtube fiend. :lolflag:

thanks for the help guys.

---

