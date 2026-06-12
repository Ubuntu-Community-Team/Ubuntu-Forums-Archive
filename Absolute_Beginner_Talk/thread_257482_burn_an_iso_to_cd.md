---
title: "burn an iso to cd?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-09-14
Hi,
How do I burn an iso file to a cd in ubuntu?

thanks for any help!

---

### Post by nickburns on 2006-09-14
All you have to do is right click the file and select the burn to CD option.

---

### Post by confused57 on 2006-09-14
Here's an excellent "HowTo":

[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

You should(or take your chances) do a md5sum check of the iso to ensure that it downloaded correctly, with no corruption.  Burn it "as an image", not as a data cd or a bootable cd, and burn it at a low speed(8x or less).

---

### Post by Marsolin on 2006-09-14
The easiest way is to use a program like [K3B]("http://linuxappfinder.com/package/k3b"), [Bonfire]("http://linuxappfinder.com/package/bonfire"), [GnomeBaker]("http://linuxappfinder.com/package/gnomebaker"), or [Graveman]("http://linuxappfinder.com/package/graveman"). I prefer K3b.

In each of those you can select to write/burn a drive image/iso. Insert a blank disk, select the iso file, click to burn, and then just sit back and wait until it's done.

---

