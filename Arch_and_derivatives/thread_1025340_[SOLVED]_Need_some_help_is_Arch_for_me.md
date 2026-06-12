---
title: "[SOLVED] Need some help: is Arch for me?"
date: 2008-12-30
forum: Arch and derivatives
---

### Post by Open-SuSe-A-Me on 2008-12-30
Hello, I am thinking of giving Arch a try on my laptop due to the positive reviews it has on here, but i have a few major questions:

1.  Can anyone vouch for the "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)"?  I wont go into detail, but every distro i have tried (many) gets choppy video, apparently due to the Intel driver forcing "Textured Video" which does not work well with this card.  The only distros that work are Hardy and Opensuse (Cant use Intrepid because of this also).  I have confirmed through testing that this setting in the driver is the culprit.  

2.  How is KDE3 in Arch? I love both Gnome and KDE but i can't tolerate KDE4, and i know alot of the distros now ship KDE4 default.  I'm not very fond of Kubuntu or Lenny(hardware support reasons), and i would love to be able to use KDE3 again.

3.  Is synaptics touchpad support good?  It bothers me that its so easy in Ubuntu to mess with the tapping/scrolling settings, but other distros have no "touchpad" menu in the mouse settings, and the new "xorg" has raped the user's control away.

4.  What is KDEmod?  Is it better?

---

### Post by fwojciec on 2008-12-30
1. I know there were issues with intel driver, since it is undergoing heavy development, but people who have tried the latest kernel/xorg/intel driver (git versions) were stunned by how good the performance was -- see this [thread](http://bbs.archlinux.org/viewtopic.php?id=61650) -- so things are looking up for intel video users.

2. There is no official KDE3 in Arch anymore -- but I think kdemod project provides it.

3. All Arch gives you is the latest drivers and software.  You can set it up the way you want it.  There are not GUIs to configure it installed by default, if this is what you're asking, because by default you get the command line, a package manager and that's it.

4. It's a matter of taste.

---

### Post by kerry_s on 2008-12-30
you do know arch is a do it your self deal?
i very much doubt arch is for you from your other questions.

1. if you know the cause, it's simple disable.

2. nada

3. only if you set it up right

4. nada

---

### Post by Open-SuSe-A-Me on 2008-12-30
Wow thanks for the quick replies..

Yes i know that Arch is a do-it-yourself with selecting packages, but i would assume that if i installed Gnome it would have the same GUI tools in the System menu no?

I'm happy with Ubuntu, but i've been searching for a solid KDE3 distro and Arch seemed to be one of them.

I would be using Opensuse with kDE3 but oddly it had audio skipping problems for me, even the people with 10 million posts on their forums had no idea why after a week of trying to help me.

Thanks!

---

### Post by Rokurosv on 2008-12-30
KDEmod is KDE 3 and 4 modified for Chakra, an Arch KDE Live CD, so they're sorta 'optimized' for Arch. I think KDE 3 is in the KDEmod repositories. I used KDEmod's KDE 4 and it worked fine, some minor issues but those were graphic card related.

---

### Post by fwojciec on 2008-12-30
> **Open-SuSe-A-Me said:**
> Yes i know that Arch is a do-it-yourself with selecting packages, but i would assume that if i installed Gnome it would have the same GUI tools in the System menu no?

You'd only get what Gnome includes in its default configuration -- there are no Arch specific enhancements.

---

### Post by Nepherte on 2008-12-30
You don't have to worry about 1 & 3. I have them and it works just fine.

---

### Post by crimesaucer on 2008-12-30
You will probably have to configure your synaptics driver in xorg.conf:


[http://wiki.archlinux.org/index.php/Synaptics](http://wiki.archlinux.org/index.php/Synaptics)



I haven't a clue about anything KDE....

---

### Post by smartboyathome on 2008-12-30
> **Nepherte said:**
> You don't have to worry about 1 & 3. I have them and it works just fine.

Ditto from me. I have a laptop with an Intel x3100, and it works great. I don't use any compositing like Compiz though, so that could be part of the reason why it works fine for me. ;)

---

### Post by billgoldberg on 2008-12-30
> **Open-SuSe-A-Me said:**
> Wow thanks for the quick replies..

Yes i know that Arch is a do-it-yourself with selecting packages, but i would assume that if i installed Gnome it would have the same GUI tools in the System menu no?



Nope.

If you want some of those programs Ubuntu installs by default, you'll need to install them yourselfs.

For example, by default you can't edit the gnome menu after you installed it.

You'll need to install "alacarte" for that.

---

### Post by doorknob60 on 2008-12-30
2. KDE3: [http://kdemod.ath.cx/download-kdemod3.html](http://kdemod.ath.cx/download-kdemod3.html)
4. If you want KDE3, then yes it's better. For KDE4, KDEmod and standard KDE both work fine, but I use KDEmod stuff because I only have some KDE stuff installed (Konqueror, Ktorrent, Kolourpaint, etc.)

---

### Post by Open-SuSe-A-Me on 2008-12-31
Thanks for all of the information, I'll be giving it a try shortly, and hopefully learn a whole lot in the process.

I'm assuming i will have to modify grub manually for it to recognize my XP partition right?

---

### Post by crimesaucer on 2008-12-31
> **Open-SuSe-A-Me said:**
> Thanks for all of the information, I'll be giving it a try shortly, and hopefully learn a whole lot in the process.

I'm assuming i will have to modify grub manually for it to recognize my XP partition right?

All you will to do is uncomment the Windows section when you edit the grub menu.lst file.

---

### Post by gjoellee on 2008-12-31
> **fwojciec said:**
> 
2.but I think kdemod project provides it.


yes KDEmod offers KDE3, KDE 4.1.3 and KDE 4.2 development, which had more the functionality of KDE3.

If you want to read more about Arch Linux this page might be something: [http://kshoster.net/content/arch-linux](http://kshoster.net/content/arch-linux)

---

### Post by Open-SuSe-A-Me on 2008-12-31
Okay i guess i botched my first attempt, then i realized i was using the "install guide" instead of the "beginners guide".


Grub was surprisingly easy to configure, i actually figured it out by myself - woo!

When i got to "pacman -Sy" it wouldnt connect to any of the servers, i must have missed something even though the network set up in the beginning said DCHP was configured.  I'm sure the beginners guide has something in it i missed.

---

### Post by crimesaucer on 2008-12-31
> **Open-SuSe-A-Me said:**
> Okay i guess i botched my first attempt, then i realized i was using the "install guide" instead of the "beginners guide".


Grub was surprisingly easy to configure, i actually figured it out by myself - woo!

When i got to "pacman -Sy" it wouldnt connect to any of the servers, i must have missed something even though the network set up in the beginning said DCHP was configured.  I'm sure the beginners guide has something in it i missed.

Did you do the FTP install?

---

### Post by Open-SuSe-A-Me on 2008-12-31
I tried the FTP/HTTP option at first because i have a good connection, but every single server would say "error connecting" so i used the packages on the cd.  Then once i rebooted and tried to update i got errors.  I probably forgot to edit one of the config files.

---

### Post by fwojciec on 2008-12-31
Sounds like your network connection is not configured correctly.  Cable?  Wireless?  If wireless then you shouldn't really expect it to work out of the box -- it needs to be properly configured first.  See the wiki -- [http://wiki.archlinux.org/index.php/Beginners_Guide#Configuring_the_network_.28if_necessary.29]("http://wiki.archlinux.org/index.php/Beginners_Guide#Configuring_the_network_.28if_necessary.29")

---

### Post by Open-SuSe-A-Me on 2008-12-31
Ok i got kdemod3-vanilla up and running and all i could say was WOW! i can believe how fast it is.

BUT - the concern in my original post is present: video tearing.  The workaround for this problem (which works in every distro that has this problem) is to use Mplayer from the terminal and force the video through the Overlay port (82 in my case) - 
mplayer file.mpg -vo xv:port=<port> 
The website that has this solution ([http://www.gossamer-threads.com/lists/mythtv/users/342092](http://www.gossamer-threads.com/lists/mythtv/users/342092))  suggests rebuilding the Intel video driver with a .diff patch located on that site, and then adding "XvPreferOverlay" "true" to the device section in xorg.conf.

Is there a way to force Overlay for all players in Xorg without rebuilding the driver?

Also, is there a package to change the theme of GTK apps like firefox? I know in Lenny w/KDE i had to install the "geramik" package to match the keramik theme i use.  Without the package GTK apps look like they are GTK1 instead of 2.

Package "amarok" not found in pacman? - Edit: Nevermind,i found amarok.

Thanks!

---

### Post by Dr Small on 2008-12-31
> **Open-SuSe-A-Me said:**
> 
Package "amarok" not found in pacman?



```
[drsmall@darkghost ~]$ pacman -Ss amarok
extra/amarok-base 1.4.10-1
    amaroK - a media player for KDE
extra/amarok-engine-xine 1.4.10-1
    xine engine for amaroK
community/exaile 0.2.14-2
    A media player aiming to be similar to KDE's AmaroK, but for GTK+

```

---

### Post by Open-SuSe-A-Me on 2009-01-01
any ideas?

---

### Post by fwojciec on 2009-01-01
I'm not going to explain everything about makepkg/ABS -- there are wikis: [http://wiki.archlinux.org/index.php/ABS](http://wiki.archlinux.org/index.php/ABS), [http://wiki.archlinux.org/index.php/Makepkg](http://wiki.archlinux.org/index.php/Makepkg)

So -- your best bet is to rebuild the xf86-video-intel package with the patch you mention.  It's easy -- being able to rebuild and customize packages is one of things Arch excels at...  Here is, roughly, what you need to do:

1) Copy xf86-video-intel PKGBUILD and the accompanying files from abs tree to a build directory somewhere (I use /var/abs/local/[pkgname] for this but it's just as well if you use something in your home dir for example).
2) Download and copy the patch you mentioned earlier to the same directory as the PKGBUILD file.
3) Use this customized PKGBUILD (notice that I edited it to include the patch you mention.)

```
# $Id$
# Maintainer: Alexander Baldeck <alexander@archlinux.org>
# Maintainer: Jan de Groot <jgc@archlinux.org>
pkgname=xf86-video-intel
pkgver=2.4.3
pkgrel=1
pkgdesc="X.org Intel i810/i830/i915/945G/G965+ video drivers"
arch=(i686 x86_64)
url="http://xorg.freedesktop.org/"
depends=('intel-dri>=7.2' 'libpciaccess>=0.10.5' 'libdrm>=2.3.1')
makedepends=('pkgconfig' 'xorg-server>=1.5.3' 'xf86driproto>=2.0.4' 'glproto>=1.4.9' 'mesa>=7.2' 'libdrm=2.3.1')
conflicts=('xorg-server<1.5.3' 'xf86-video-i810')
replaces=('xf86-video-i810')
options=('!libtool' 'force')
groups=('xorg-video-drivers')
source=(${url}/releases/individual/driver/${pkgname}-${pkgver}.tar.bz2
	intel-prefer-hardware-overlay.diff
    20_thinkpad_g40_quirk.patch
	21_quirk_lenovo.patch
	23_quirks_studiohybrid_eeepc_and_w251u.patch
	25_quirk_nc6110.patch
	26_i830-use-lfp-data-ptrs.patch
	27_disable_fbc_on_965.patch)

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  patch -Np1 -i "${srcdir}/intel-prefer-hardware-overlay.diff" || return 1
  patch -Np1 -i "${srcdir}/20_thinkpad_g40_quirk.patch" || return 1
  patch -Np1 -i "${srcdir}/21_quirk_lenovo.patch" || return 1
  patch -Np1 -i "${srcdir}/23_quirks_studiohybrid_eeepc_and_w251u.patch" || return 1
  patch -Np1 -i "${srcdir}/25_quirk_nc6110.patch" || return 1
  patch -Np1 -i "${srcdir}/26_i830-use-lfp-data-ptrs.patch" || return 1
  patch -Np1 -i "${srcdir}/27_disable_fbc_on_965.patch" || return 1
  ./configure --prefix=/usr \
              --enable-dri || return 1
  make || return 1
  make DESTDIR="${pkgdir}" install || return 1
}
md5sums=('a664819288b98a37f77ab6ae1e14c9d9'
         '1b680981280711dea7c239b351212512'
         '68a362a168ffa4f37d9f722f43855468'
         '2d617364ac2e47ca366901d0b849b1a1'
         '3d0f8e593e8eac3000154feb6b0f45b8'
         '3deb800906e6845e8576d4e9d0f22b12'
         'cb7ee7a68858c038020e0cd991143d8e'
         'd215e428585c6e55aefd9f525ebfbe7b')
```


4) Build and install your customized version of intel driver.

---

### Post by gjoellee on 2009-01-01
> **Open-SuSe-A-Me said:**
> 
When i got to "pacman -Sy" it wouldnt connect to any of the servers, i must have missed something even though the network set up in the beginning said DCHP was configured.  I'm sure the beginners guide has something in it i missed.

have you tried starting dhcp again? ```
dhcpcd eth0
```

---

### Post by Open-SuSe-A-Me on 2009-01-01
> **fwojciec said:**
> I'm not going to explain everything about makepkg/ABS -- there are wikis: [http://wiki.archlinux.org/index.php/ABS](http://wiki.archlinux.org/index.php/ABS), [http://wiki.archlinux.org/index.php/Makepkg](http://wiki.archlinux.org/index.php/Makepkg)

So -- your best bet is to rebuild the xf86-video-intel package with the patch you mention.  It's easy -- being able to rebuild and customize packages is one of things Arch excels at...  Here is, roughly, what you need to do:

1) Copy xf86-video-intel PKGBUILD and the accompanying files from abs tree to a build directory somewhere (I use /var/abs/local/[pkgname] for this but it's just as well if you use something in your home dir for example).
2) Download and copy the patch you mentioned earlier to the same directory as the PKGBUILD file.
3) Use this customized PKGBUILD (notice that I edited it to include the patch you mention.)

```
# $Id$
# Maintainer: Alexander Baldeck <alexander@archlinux.org>
# Maintainer: Jan de Groot <jgc@archlinux.org>
pkgname=xf86-video-intel
pkgver=2.4.3
pkgrel=1
pkgdesc="X.org Intel i810/i830/i915/945G/G965+ video drivers"
arch=(i686 x86_64)
url="http://xorg.freedesktop.org/"
depends=('intel-dri>=7.2' 'libpciaccess>=0.10.5' 'libdrm>=2.3.1')
makedepends=('pkgconfig' 'xorg-server>=1.5.3' 'xf86driproto>=2.0.4' 'glproto>=1.4.9' 'mesa>=7.2' 'libdrm=2.3.1')
conflicts=('xorg-server<1.5.3' 'xf86-video-i810')
replaces=('xf86-video-i810')
options=('!libtool' 'force')
groups=('xorg-video-drivers')
source=(${url}/releases/individual/driver/${pkgname}-${pkgver}.tar.bz2
	intel-prefer-hardware-overlay.diff
    20_thinkpad_g40_quirk.patch
	21_quirk_lenovo.patch
	23_quirks_studiohybrid_eeepc_and_w251u.patch
	25_quirk_nc6110.patch
	26_i830-use-lfp-data-ptrs.patch
	27_disable_fbc_on_965.patch)

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  patch -Np1 -i "${srcdir}/intel-prefer-hardware-overlay.diff" || return 1
  patch -Np1 -i "${srcdir}/20_thinkpad_g40_quirk.patch" || return 1
  patch -Np1 -i "${srcdir}/21_quirk_lenovo.patch" || return 1
  patch -Np1 -i "${srcdir}/23_quirks_studiohybrid_eeepc_and_w251u.patch" || return 1
  patch -Np1 -i "${srcdir}/25_quirk_nc6110.patch" || return 1
  patch -Np1 -i "${srcdir}/26_i830-use-lfp-data-ptrs.patch" || return 1
  patch -Np1 -i "${srcdir}/27_disable_fbc_on_965.patch" || return 1
  ./configure --prefix=/usr \
              --enable-dri || return 1
  make || return 1
  make DESTDIR="${pkgdir}" install || return 1
}
md5sums=('a664819288b98a37f77ab6ae1e14c9d9'
         '1b680981280711dea7c239b351212512'
         '68a362a168ffa4f37d9f722f43855468'
         '2d617364ac2e47ca366901d0b849b1a1'
         '3d0f8e593e8eac3000154feb6b0f45b8'
         '3deb800906e6845e8576d4e9d0f22b12'
         'cb7ee7a68858c038020e0cd991143d8e'
         'd215e428585c6e55aefd9f525ebfbe7b')
```


4) Build and install your customized version of intel driver.


Thanks so much for this info, if i can fix this my system would be perfect.  If someone could explain what i have to do a bit more n00bish that would be great, i apologize i have very little compiling/building experience.  I know HOW to compile things, but this is more advanced than i know.
I see the code you provided, should i copy and paste that or something? I dont quite understand.
Also, since this is my video driver, do i need to remove the one i have first? When i compile the new one do i have to be in text-only mode?

Thanks so much for any help you can give, I'm loving this distro atm.

---

### Post by Open-SuSe-A-Me on 2009-01-01
Ok i followed your instructions and i got to the "makepkg" step and it builds for awhile and then says bsdtar: Failed to open '/home/indrid/packages/xf86-video-intel-2.4.3-1-i686.pkg.tar.gz': Permission denied
==> ERROR: Failed to create package file.

The wiki says not to run makepkg as root so i'm not sure what i did wrong.

---

### Post by Open-SuSe-A-Me on 2009-01-01
THANK YOU! IT WORKS!

The only weird thing is when a video opens, my screen will flicker with some random color pattern for a second, but after that its fine. i can live with it, but at one point i played a video and my whole screen turned white, and i did ctrl+alt+backspace and it was still white.  Anyone know why it does that?

I also managed to get my wireless working, and i have the dreaded Atheros AR5007EG which seems to cause so much trouble for some people.

Other than that does anyone know the package to fix the theme of GTK apps in KDE? they look awful otherwise.

Thank you fwojciec and everyone else, i think i have found a permanent distro for my laptop after months of random installs.

---

