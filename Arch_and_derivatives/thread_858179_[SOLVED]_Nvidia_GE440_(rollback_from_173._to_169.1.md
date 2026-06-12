---
title: "[SOLVED] Nvidia GE440 (rollback from 173.?? to 169.12)"
date: 2008-07-13
forum: Arch and derivatives
---

### Post by SnakeHips on 2008-07-13
Hi ,i've been away from Arch for a couple of weeks ,found a lot of updates and did the pacman -Syu thing.....unfortunately it installed some new nvidia stuff (173.something) which is not compatible with my card and I need to rollback to 169.12....hope this makes sense.

From boot I can get to a root prompt and need some detailed step by step instructions how to do this.....please let me know if you need any further info and thanks for any help offered.

---

### Post by K.Mandla on 2008-07-13
Waitaminute, what kind of card is this? If it's the Geforce 440, you should be using 96xx, not the >=100-series; those drivers omit pre-FX cards.

---

### Post by SnakeHips on 2008-07-13
woops brain freeze ....it's the Geforce6200...

---

### Post by mips on 2008-07-13
> **K.Mandla said:**
> Waitaminute, what kind of card is this? If it's the Geforce 440, you should be using 96xx, not the >=100-series; those drivers omit pre-FX cards.

+1

[http://wiki.archlinux.org/index.php/Beginners_Guide#NVIDIA_Graphic_Cards](http://wiki.archlinux.org/index.php/Beginners_Guide#NVIDIA_Graphic_Cards)


> NVIDIA Graphic Cards

The NVIDIA proprietary drivers are generally considered to be of good quality, and offer 3D performance, whereas the open source nv driver offers only 2d support at this time. 

Before you configure your Graphics Card you will need to know which driver fits. Arch currently has 3 different driver packages that each match a certain subset of Cards: 

1. nvidia-71xx for very old Cards like TNT and TNT2 

[COLOR="Red"]**2. nvidia-96xx slightly newer cards up to the GF 4** [/COLOR]

3. nvidia newest GPUs after the GF 4 

Consult the NVIDIA-Homepage to see which one is for you. The difference is only for the installation; Configuration works the same with every driver. 

Select and install the appropriate NVIDIA driver for your card, e.g.: 
```
pacman -S nvidia-96xx
```

The NVIDIA package has a utility for updating your existing /etc/X11/xorg.conf for use with the NVIDIA driver: 
```
nvidia-xconfig
```

EDIT: Ignore this post, came to late after the above post.

What if you just run the config utility again?

---

### Post by YodaMstr on 2008-07-13
[http://wiki.archlinux.org/index.php/Downgrade_packages](http://wiki.archlinux.org/index.php/Downgrade_packages)

should tell you all you need about downgrading.

---

### Post by SnakeHips on 2008-07-13
Thanks i'll try the Pacman -U option....all I have to do now is find the package ,its not in /var/cache/pacman/pkg

---

### Post by SnakeHips on 2008-07-13
anyone know where to find or have the 169.12 packages

I've tried the mirrors here..
[http://wiki.archlinux.org/index.php/Downgrade_packages](http://wiki.archlinux.org/index.php/Downgrade_packages)

---

### Post by YodaMstr on 2008-07-13
I was browsing the Arch forums and found this in the Mirror Status thread.

> Info
There is a new US mirror:
[http://www.schlunix.org/archlinux](http://www.schlunix.org/archlinux)
Hint: This mirror tries to hold also version of packages which are outdated, good for downgrading.

---

### Post by MisfitI38 on 2008-07-13
Here;s the PKGBUILD 
```
# $Id: PKGBUILD 1567 2008-05-13 10:11:25Z thomas $
# Maintainer : Thomas Baechler <thomas@archlinux.org>

pkgname=nvidia
pkgver=169.12
_kernver='2.6.25-ARCH'
pkgrel=4
pkgdesc="NVIDIA drivers for kernel26."
arch=('i686' 'x86_64')
[ "$CARCH" = "i686"   ] && ARCH=x86
[ "$CARCH" = "x86_64" ] && ARCH=x86_64
url="http://www.nvidia.com/"
depends=('kernel26>=2.6.25.3-1' 'kernel26<2.6.26' 'nvidia-utils')
conflicts=('nvidia-96xx' 'nvidia-71xx' 'nvidia-legacy')
license=('custom')
install=nvidia.install
source=(http://us.download.nvidia.com/XFree86/Linux-$ARCH/${pkgver}/NVIDIA-Linux-$ARCH-${pkgver}-pkg0.run
        NVIDIA_kernel-169.12-2286310.diff)
md5sums=('e7aaca79c846e34cfe8111040bfee2d0'
         'a6b6d9d7ff0306343be3fa40e72337fd')
[ "$CARCH" = "x86_64" ] && md5sums=('843a1e8bc1923ba2e4b60f6fab31ad3b'
                                    'a6b6d9d7ff0306343be3fa40e72337fd')

build()
{
  # Extract
  cd $startdir/src/
  sh NVIDIA-Linux-$ARCH-${pkgver}-pkg0.run --extract-only
  cd NVIDIA-Linux-$ARCH-${pkgver}-pkg0
  
  # Any extra patches are applied in here...
  patch -Np0 -i ../NVIDIA_kernel-169.12-2286310.diff || return 1

  cd usr/src/nv/
  ln -s Makefile.kbuild Makefile
  make SYSSRC=/lib/modules/${_kernver}/build module || return 1
  
  # install kernel module
  mkdir -p $startdir/pkg/lib/modules/${_kernver}/kernel/drivers/video/
  install -m644 nvidia.ko $startdir/pkg/lib/modules/${_kernver}/kernel/drivers/video/

  sed -i -e "s/KERNEL_VERSION='.*'/KERNEL_VERSION='${_kernver}'/" $startdir/*.install
}

```and nvidia.install
```
# arg 1:  the new package version
post_install() {
  KERNEL_VERSION='2.6.25-ARCH'
  depmod -v $KERNEL_VERSION  > /dev/null 2>&1		 
}

# arg 1:  the new package version
# arg 2:  the old package version
post_upgrade() {
  post_install $1
  rmmod nvidia || echo 'In order to use the new nvidia module, exit Xserver and unload it manually.'
}

# arg 1:  the old package version
post_remove() {
  KERNEL_VERSION='2.6.25-ARCH'
  depmod -v $KERNEL_VERSION	 > /dev/null 2>&1	 
}

op=$1
shift
$op $*
```
Save them to a build directory and do 'makepkg -c'
Then install with pacman -U
Edit: Forgot to mention. Be sure to downgrade nvidia-utils as well. ;)

---

### Post by SnakeHips on 2008-07-26
ok i'm out of my depth on this one but gonna try as 
I cant find the packages anywhere....so far i've

1. created a builds directory
2. created a file (pasted content) called PKGBUILDS and made executable
3. created a file (pasted content) called nvidia.install and made executable

then run makepkg -c with the following ,it builds to 100% and then says...
---> error: Nvidia_kernel-169.12-2286310.diff was not found in build directory
and is not a url

any ideas? or if anyone has these packages :-)

---

### Post by fwojciec on 2008-07-26
You can get the file from [here]("http://www.nvnews.net/vbulletin/showthread.php?t=110088") -- just put it in the same directory as the PKGBUILD.  The PKGBUILD and nvidia.install do not need to be executable, btw.

Just to warn you -- the kernel is about to be updated to 2.6.26 version, which means you *will* be forced to redo all this work when you install the new kernel, and each new kernel after that.  That is assuming that the 169 driver even compiles using the latest kernel...

What I'm trying to say is that the solution you're determined to realize is not going to work as the permanent solution for Arch -- in fact a rolling release distro might be a bad choice for you if this driver is the only thing that makes your video card work properly.

---

### Post by YodaMstr on 2008-07-26
Couldn't he add the kernel to the HoldPkg line in his pacman.conf?

---

### Post by fwojciec on 2008-07-26
> **YodaMstr said:**
> Couldn't he add the kernel to the HoldPkg line in his pacman.conf?

This is, of course, an option, but it's only a means of postponing the inevitable.  Eventually packages from the repos will begin to depend on more recent versions of the kernel.

I'm not saying that it is impossible to run an older version of nvidia drivers in Arch, but I don't think it is possible easily, without having to occasionally customize and rebuild some official packages.

---

### Post by cardinals_fan on 2008-07-27
My 6100 is also broken with the new drivers, but the legacy (96-xx) works fine.

---

### Post by SnakeHips on 2008-07-27
> **fwojciec said:**
> You can get the file from [here]("http://www.nvnews.net/vbulletin/showthread.php?t=110088") -- just put it in the same directory as the PKGBUILD.  The PKGBUILD and nvidia.install do not need to be executable, btw.

Just to warn you -- the kernel is about to be updated to 2.6.26 version, which means you *will* be forced to redo all this work when you install the new kernel, and each new kernel after that.  That is assuming that the 169 driver even compiles using the latest kernel...

What I'm trying to say is that the solution you're determined to realize is not going to work as the permanent solution for Arch -- in fact a rolling release distro might be a bad choice for you if this driver is the only thing that makes your video card work properly.

Thanks for your post

You're probably right ,Arch is a little advanced for me but I love the distro and the ethos that goes with it....moving forward I guess the short answer would be to upgrade to a video card supported by the 173. driver
- i'll look into that.

For now though the build fails with -
PKGBUILD line32: patch: command not found

I can see that it's something to do with the .diff file but have'nt a clue what to do??

---

### Post by fwojciec on 2008-07-27
> **SnakeHips said:**
> Thanks for your post

You're probably right ,Arch is a little advanced for me but I love the distro and the ethos that goes with it....moving forward I guess the short answer would be to upgrade to a video card supported by the 173. driver
- i'll look into that.

For now though the build fails with -
PKGBUILD line32: patch: command not found

I can see that it's something to do with the .diff file but have'nt a clue what to do??

That means that makepkg can't find the "patch" program.  You probably need to install "base-devel" group of packages (just do pacman -Sy base-devel), which includes patch and many other useful things.

---

### Post by SnakeHips on 2008-07-29
Ok I tried to build the package and now give up lol.....I now want to put Arch into *vesa* mode and ignore the nvidia module/driver ,what do I have to do please.

Thanks for everyones help.

---

### Post by mips on 2008-07-29
If the vesa driver is still installed you should be able to simply specify vesa instead of nvidia in the xorg.conf

Or uninstalle the nvidia driver and simply run the xorg conf utility again.

---

### Post by SnakeHips on 2008-07-29
Ok ,i've got this working in 'vesa' mode now and going to follow Cardinals' lead and use 96xx. UPDATE - works fine after nvidia-xconfig :-)

found this:
By using this package you accept the NVIDIA license,
which has been installed in /usr/share/licenses/nvidia/LICENSE
If you do not accept this license, you must remove the package immediately.
Dont forget to update your /etc/X11/xorg.conf
In order to use nvidia-settings, you need to install the gtk2 package.
In order to use nvidia-xconfig, you need to install the pkgconfig package.
-------------------------------
nvidia 9746 drops support for Geforce 3 and 4 cards
If you have such a card, install the nvidia-96xx, nvidia-96xx-utils,
nvidia-96xx-ck, nvidia-96xx-beyond, nvidia-96xx-suspend2 packages
For a list of supported cards, see /usr/share/doc/nvidia/supported-cards.txt

---

