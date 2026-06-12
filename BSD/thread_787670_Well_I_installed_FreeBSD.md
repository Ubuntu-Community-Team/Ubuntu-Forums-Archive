---
title: "Well I installed FreeBSD"
date: 2008-05-09
forum: BSD
---

### Post by MONODA on 2008-05-09
I just installed FreeBSD 7.0 and it is quite fast and seems nice and that I will have to learn quite a lot.  I have a few questions,
1. I am running KDE, how can I get it to automout external devices?
2. How do I install (search and remove) packages? 
3. My sound is not working, I get an error:
> Error while initializing the sound driver:

device /dev/dsp can't be opened (no such fle or directory)
how can I fix it?

I know I should ask this on a BSD forum but all the posts on bsdforums.org seem to be related to pornography... thanks anyway
one more thing, what are some cool things i should check out (I am a command line junkie XD)

---

### Post by MONODA on 2008-05-09
I just tried to boot into my archlinux system on the same drive (but of course different partition) but it did not have a section for it, where is the menu.lst equivilant for FreeBSD? Also, for some reason my SCSI drives look like IDE drives (ad4 is the name of my drive in FreeBSD)

---

### Post by MONODA on 2008-05-09
I also realized that my wireless doesnt work and I dont have access to a wired network at the moment (I am using my bros laptop to type this)

---

### Post by cardinals_fan on 2008-05-09
Install packages with pkg_add.  The [FreeBSD Handbook]("http://www.freebsd.org/doc/en/books/handbook/") is great.  I recommend booting a Puppy Live CD and running the GRUB install app - it works very well.  It might help if you could post some info on your wireless card.

By the way, the BSDnexus forums are pretty good if small: [http://forums.bsdnexus.com/](http://forums.bsdnexus.com/).

---

### Post by MONODA on 2008-05-10
well I have an Intel Pro wireless 3945 ABG. I noticed that the driver isnt included in the set of cds and that it is not available for OpenBSD.

---

### Post by cardinals_fan on 2008-05-10
> **MONODA said:**
> well I have an Intel Pro wireless 3945 ABG. I noticed that the driver isnt included in the set of cds and that it is not available for OpenBSD.
[http://www.openbsd.org/cgi-bin/man.cgi?query=wpi](http://www.openbsd.org/cgi-bin/man.cgi?query=wpi)

The wpi driver looks like the one you want.  According to the FreeBSD 7.0 release notes, wpi is included: > [amd64, i386] The wpi(4) driver has been added to support the Intel 3945 Wireless LAN Controller.
What are the results of ifconfig wpi0?  Read here: [http://www.freebsd.org/cgi/man.cgi?query=wpi&sektion=4&manpath=FreeBSD+7.0-RELEASE](http://www.freebsd.org/cgi/man.cgi?query=wpi&sektion=4&manpath=FreeBSD+7.0-RELEASE)

---

### Post by Iandefor on 2008-05-10
> **MONODA said:**
> I just installed FreeBSD 7.0 and it is quite fast and seems nice and that I will have to learn quite a lot.  I have a few questions,
1. I am running KDE, how can I get it to automout external devices?
2. How do I install (search and remove) packages? 
3. My sound is not working, I get an error:

how can I fix it?

I know I should ask this on a BSD forum but all the posts on bsdforums.org seem to be related to pornography... thanks anyway
one more thing, what are some cool things i should check out (I am a command line junkie XD)1. Try poking around in /usr/local/etc/dbus-1. I was having problems with automounting and it turned out dbus by default doesn't grant you permission to send messages to HAL.
2. You can use ports or the pkg_add command (pkg_add -r [name of package] is what you want to remotely fetch the package). Ports will download and compile the software, pkg_add uses FreeBSD's binary packaging system to install it.
3. Check out the [relevant section in the FreeBSD Handbook]("http://www.freebsd.org/doc/en/books/handbook/sound-setup.html").
> **MONODA said:**
> I just tried to boot into my archlinux system on the same drive (but of course different partition) but it did not have a section for it, where is the menu.lst equivilant for FreeBSD? Also, for some reason my SCSI drives look like IDE drives (ad4 is the name of my drive in FreeBSD)I recommend reinstalling GRUB and adding a menu entry for FreeBSD. The archlinux wiki has a useful [howto]("http://wiki.archlinux.org/index.php/Reinstalling_GRUB"). To add an entry for FreeBSD, you can do something like:
```

title   FreeBSD
root  (hdsomething,something)
chainloader +1
boot
```

---

### Post by MONODA on 2008-05-11
thanks for your help, I got grub working, now to get automounting to work.

---

