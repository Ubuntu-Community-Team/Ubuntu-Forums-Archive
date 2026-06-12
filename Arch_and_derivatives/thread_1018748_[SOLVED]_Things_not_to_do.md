---
title: "[SOLVED] Things not to do?"
date: 2008-12-22
forum: Arch and derivatives
---

### Post by linkmaster03 on 2008-12-22
When I install stuff, I always seem to get anxious and do something dumb, or take the quick and easy route. I want Arch to be something that I will stick with, and not get clogged with crap. (like Ubuntu) Is there anything that I should do (or know) on installation to keep Arch running slick for years to come?

---

### Post by OutOfReach on 2008-12-22
You mean you want to keep it as lean as possible?
Well, all I can say is install and enable (daemons) only what you need. Maybe someone else has better advice.

---

### Post by Xiong Chiamiov on 2008-12-22
The very nature of Arch means that you'll probably be fine.  Besides, you have very good control over what daemons run, and if you remove packages and leave things behind, pacman has pretty good orphan-finding ability.

---

### Post by will1911a1 on 2008-12-22
My advice: Don't worry too much about it.  Pacman makes it so easy to remove things that even if you install something you decide you don't want later, you can get rid of it with no problem.

Just being in the mindset that you don't want to clog everything up should help you out a lot.

---

### Post by linkmaster03 on 2008-12-22
I hear programs compiled from source can be managed as packages (or something like that) through pacman. I'm used to ./configure && make && sudo make install. How exactly does this work?

---

### Post by smartboyathome on 2008-12-22
> **linkmaster03 said:**
> I hear programs compiled from source can be managed as packages (or something like that) through pacman. I'm used to ./configure && make && sudo make install. How exactly does this work?

Just make a PKGBUILD, and then run makepkg PKGBUILD. Heres a copy of my PKGBUILD for NtEd, which basically does what you want. Remember to keep track of dependancies. ;)

```
# Contributor: Alex Abbott <smartboyathome@gmail.com>

pkgname=nted
pkgver=1.4.17
pkgrel=2
pkgdesc="A WYSIWYG Music Notation program with an aim toward user friendliness." 
arch=(i686 x86_64)
url="http://vsr.informatik.tu-chemnitz.de/staff/jan/nted/nted.xhtml" 
license="GPL" 
depends=('pkgconfig' 'automake' 'gtk2' 'cairo') 
source=(http://vsr.informatik.tu-chemnitz.de/staff/jan/nted/$pkgname-$pkgver.tar.gz)
md5sums=('a1342ae8cff7bceb7ed9ee1f38294753')

build() { 
	cd $srcdir/$pkgname-$pkgver
	./configure --prefix=/usr
	make || return 1
	make DESTDIR=$pkgdir install || return 1

}
```

---

### Post by OutOfReach on 2008-12-22
Might want to reference [this]("http://wiki.archlinux.org/index.php/ABS") for a complete explanation.

---

### Post by crimesaucer on 2008-12-22
> **linkmaster03 said:**
> I hear programs compiled from source can be managed as packages (or something like that) through pacman. I'm used to ./configure && make && sudo make install. How exactly does this work?

People can build packages from source in Archlinux in a few different ways:

A.) Use a PKGBUILD from the ABS tree.
B.) Use a PKGBUILD from the AUR tarball.
C.) Write a PKGBUILD of your own using the PKGBUILD/pkg.install templates and the wiki page for help.
D.) You can build a pkg with the old ./configure && make && sudo make install way.

With options A, B, and C you build the package with the simple command "makepkg -c" (make the package "clean")..... then you install the package with the command "sudo pacman -U builtpackage-x86_64.pkg.tar.gz".

---

### Post by linkmaster03 on 2008-12-22
Thanks guys. The last thing is: what is the probability of encountering malicious PKGBUILD's from AUR?

---

### Post by SomeGuyDude on 2008-12-22
> **linkmaster03 said:**
> Thanks guys. The last thing is: what is the probability of encountering malicious PKGBUILD's from AUR?

Zero. Since it's democratic, malicious packages get annihilated. Read the comments if you're unsure about anything.

---

### Post by linkmaster03 on 2008-12-22
Thanks everyone. I'll be downloading the installation CD, preparing my partitions, and installing Arch when I get back from the holidays. :)

---

### Post by Xiong Chiamiov on 2008-12-24
I wouldn't say it's zero, but it's pretty darn close.

BTW, OP, you'll probably want to use Yaourt to access things from the AUR.  Aside from being amazing, it allows you to edit (or at least view) pkgbuilds very easily before installing them.

---

### Post by linkmaster03 on 2008-12-24
Xiong Chiamiov: Thanks for the tip! I was wondering what yaourt was.

---

### Post by handy on 2008-12-25
Throw any unfamiliar names at the [***_Arch repo' search field_***]("http://www.archlinux.org/packages/?sort=-last_update") & also search the [***_AUR_***]("http://aur.archlinux.org/packages.php").

I use those as a kind of Arch package name dictionary, it is more effective than Scroogle I find.

---

### Post by fwojciec on 2008-12-27
> **linkmaster03 said:**
> Thanks guys. The last thing is: what is the probability of encountering malicious PKGBUILD's from AUR?

This is generally considered a real possibility, though it's unlikely that a malicious PKGBUILD go on unnoticed for a long time.  This, incidentally, is also the main reason why programs like yaourt are never going to be included in the community repo for easy installation with pacman: installing packages from AUR should not be something you just click/enter through without thinking what it is you're actually installing.

---

