---
title: "pacman error"
date: 2009-02-01
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-01
i installed archlinux and then configured pacman.then,i typed in
pacman -Syu to upgrade my system,it showed that it was successfully connected to the proxy server,and then i was asked a few questions,and i answered all with yes,and then pacman stated that it had detected a new version of itself,i said yes to that upgrade,and i easily upgraded pacman this way,which was followed by coming back to the root shell.Now,i typed again pacman -Syu.This time too it connected to the proxy server,but got stuck at a point saying"trying to login as anonymous".how do i solve this?

---

### Post by LinuxGuy1234 on 2009-02-01
> **stonecoldjha said:**
> i installed archlinux and then configured pacman.then,i typed in
pacman -Syu to upgrade my system,it showed that it was successfully connected to the proxy server,and then i was asked a few questions,and i answered all with yes,and then pacman stated that it had detected a new version of itself,i said yes to that upgrade,and i easily upgraded pacman this way,which was followed by coming back to the root shell.Now,i typed again pacman -Syu.This time too it connected to the proxy server,but got stuck at a point saying"trying to login as anonymous".how do i solve this?

[File a Arch Linux bug report. Include as much info as possible. Make sure that the package is "Pacman".]("http://bugs.archlinux.org/")

---

### Post by stonecoldjha on 2009-02-01
are you sure that is a bug?

---

### Post by Rumor on 2009-02-01
I'd check your /etc/pacman.d/mirrorlist file before filing any bug reports. It sounds to me like pacman is trying to access ftp.archlinux.org rather than your closest / fastest repository.

I had this same thing crop up on a recent install, and simply moving my preferred repositories to the top of the list took care of it.

---

### Post by ubersolid on 2009-02-01
when you update pacman it overwrites your mirrorlist with a default one, and the default is indeed ftp.archlinux.org.
fix it by copying over /etc/pacman.d/mirrorlist.pacorig (this is the backup) to /etc/pacman.d/mirrorlist
```
cp /etc/pacman.d/mirrorlist.pacorig /etc/pacman.d/mirrorlist
```

---

### Post by crimesaucer on 2009-02-01
> **ubersolid said:**
> when you update pacman it overwrites your mirrorlist with a default one, and the default is indeed ftp.archlinux.org.
fix it by copying over /etc/pacman.d/mirrorlist.pacorig (this is the backup) to /etc/pacman.d/mirrorlist
```
cp /etc/pacman.d/mirrorlist.pacorig /etc/pacman.d/mirrorlist
```

Or just #comment the mirrors that you don't use. 


The even better thing to do is to run the "rankmirrors" command in the terminal:

```
rankmirrors -v
```

then copy the output into your /etc/mirrorlist.... it should be in the order of the fastest mirror at the top to the slowest at the bottom.


It should look something like this (it will be a different order for a different location, I live in the NOVA/D.C. area so these are my closest mirrors):

```

Server = http://mirror.umoss.org/archlinux/$repo/os/x86_64
Server = http://mirror.rit.edu/archlinux/$repo/os/x86_64
Server = http://mirrors.gigenet.com/archlinux/$repo/os/x86_64
Server = ftp://mirrors.portafixe.com/archlinux/$repo/os/x86_64
Server = ftp://mirror.cs.vt.edu/pub/ArchLinux/$repo/os/x86_64
Server = http://mirrors.easynews.com/linux/archlinux/$repo/os/x86_64
Server = http://mirror2.archlinux.com.ve/$repo/os/x86_64
Server = http://mirror.archlinux.com.ve/$repo/os/x86_64
Server = http://mirror.neotuli.net/arch/$repo/os/x86_64
Server = http://archlinux.mirrors.uk2.net/$repo/os/x86_64
Server = http://schlunix.org/archlinux/$repo/os/x86_64
Server = http://www.mirrorservice.org/sites/ftp.archlinux.org/$repo/os/x86_64
Server = http://ftp.uni-kl.de/pub/linux/archlinux/$repo/os/x86_64
Server = ftp://ftp.archlinux.org/$repo/os/x86_64
Server = http://archlinux.unixheads.org/$repo/os/x86_64
Server = http://mir.archlinux.fr/$repo/os/x86_64
Server = http://archlinux.c3sl.ufpr.br/$repo/os/x86_64
Server = http://archlinux.puzzle.ch/$repo/os/x86_64
Server = http://mirror.archlinux.no/$repo/os/x86_64
Server = http://archlinux.freeside.ru/$repo/os/x86_64
Server = ftp://mirrors.uk2.net/pub/archlinux/$repo/os/x86_64
Server = ftp://mir2.archlinuxfr.org/archlinux/$repo/os/x86_64
Server = ftp://mirror.lividpenguin.com/pub/archlinux/$repo/os/x86_64
Server = ftp://locke.suu.edu/linux/dist/archlinux/$repo/os/x86_64
Server = ftp://mirrors.igprolin-online.org/archlinux/$repo/os/x86_64
Server = http://unix.net.pl/archlinux.org/$repo/os/x86_64
Server = ftp://ftp.hosteurope.de/mirror/ftp.archlinux.org/$repo/os/x86_64
Server = http://mirror.internode.on.net/pub/archlinux/$repo/os/x86_64
Server = ftp://ftp.free.fr/mirrors/ftp.archlinux.org/$repo/os/x86_64
Server = ftp://ftp.tu-chemnitz.de/pub/linux/archlinux/$repo/os/x86_64
Server = ftp://archlinux.c3sl.ufpr.br/archlinux/$repo/os/x86_64
Server = ftp://ftp.heanet.ie/mirrors/ftp.archlinux.org/$repo/os/x86_64
Server = ftp://mir1.archlinuxfr.org/archlinux/$repo/os/x86_64
Server = ftp://ftp.surfnet.nl/pub/os/Linux/distr/archlinux/$repo/os/x86_64
Server = ftp://ftp.sh.cvut.cz/MIRRORS/arch/$repo/os/x86_64
Server = ftp://ftp.nluug.nl/pub/metalab/distributions/archlinux/$repo/os/x86_64
Server = ftp://ftp.estpak.ee/pub/archlinux/$repo/os/x86_64
Server = ftp://ftp5.gwdg.de/pub/linux/archlinux/$repo/os/x86_64
Server = ftp://ftp.klid.dk/archlinux/$repo/os/x86_64
Server = ftp://ftp-stud.hs-esslingen.de/pub/Mirrors/archlinux/$repo/os/x86_64
Server = ftp://ftp.ds.hj.se/pub/os/linux/archlinux/$repo/os/x86_64
Server = ftp://mi.mirror.garr.it/mirrors/archlinux/$repo/os/x86_64
Server = ftp://ftp.mfa.kfki.hu/pub/mirrors/ftp.archlinux.org/$repo/os/x86_64
Server = http://mirror.isoc.org.il/pub/archlinux/$repo/os/x86_64
Server = ftp://distrib-coffee.ipsl.jussieu.fr/pub/linux/archlinux/$repo/os/x86_64
Server = ftp://archlinux.hell.org.ua/archlinux/$repo/os/x86_64
Server = ftp://mirror.yandex.ru/archlinux/$repo/os/x86_64
Server = ftp://ftp.las.ic.unicamp.br/pub/archlinux/$repo/os/x86_64
Server = ftp://mirror.icis.pcz.pl/archlinux/$repo/os/x86_64
Server = ftp://ftp.rez-gif.supelec.fr/Linux/archlinux/$repo/os/x86_64
Server = ftp://ftp.iasi.roedu.net/mirrors/archlinux.org/$repo/os/x86_64
Server = ftp://ftp.belnet.be/mirror/archlinux.org/$repo/os/x86_64
Server = ftp://ftp.gtlib.gatech.edu/pub/linux/distributions/archlinux/$repo/os/x86_64
Server = ftp://ftp.linux.org.tr/pub/mirrors/archlinux/$repo/os/x86_64
Server = ftp://ftp.ntua.gr/pub/linux/archlinux/$repo/os/x86_64
Server = ftp://cesium.di.uminho.pt/pub/archlinux/$repo/os/x86_64
Server = ftp://ftp.ibiblio.org/pub/linux/distributions/archlinux/$repo/os/x86_64
Server = ftp://mirror.aarnet.edu.au/pub/archlinux/$repo/os/x86_64
Server = ftp://202.78.230.5/archlinux/$repo/os/x86_64
Server = ftp://ftp.uni-bayreuth.de/pub/linux/archlinux/$repo/os/x86_64
Server = ftp://mirror.pacific.net.au/linux/archlinux/$repo/os/x86_64
Server = ftp://mirror.csclub.uwaterloo.ca/archlinux/$repo/os/x86_64
Server = ftp://ftp.linux.kiev.ua/pub/Linux/ArchLinux/$repo/os/x86_64
Server = ftp://ftp.iinet.net.au/pub/archlinux/$repo/os/x86_64
Server = ftp://gd.tuwien.ac.at/opsys/linux/archlinux/$repo/os/x86_64
Server = http://piotrkosoft.net/pub/mirrors/ftp.archlinux.org/$repo/os/x86_64
Server = ftp://ftp.gigabit.nu/$repo/os/x86_64
Server = ftp://ftp.piotrkosoft.net/pub/mirrors/ftp.archlinux.org/$repo/os/x86_64
Server = ftp://ftp.archlinuxppc.org/x86_64/$repo/os/x86_64
Server = http://archlinux.cbn.net.id/$repo/os/x86_64
Server = http://archlinux.umflint.edu/mirrors/archlinux/$repo/os/x86_64
Server = ftp://archlinux.cbn.net.id/pub/archlinux/$repo/os/x86_64

```

---

### Post by kerry_s on 2009-02-01
on a fresh install you need to make sure you install "python" before you can use rankmirrors.

```
sudo pacman -S python
```

---

### Post by stonecoldjha on 2009-02-01
thank you to all of you,i could getit solved doing what you told.

---

