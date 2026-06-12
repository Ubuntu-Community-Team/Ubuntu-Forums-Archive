---
title: "Debian can't detect my network card"
date: 2012-06-13
forum: Any Other OS
---

### Post by tech291083 on 2012-06-13
Hi,

I have just downloaded and installed Debian 6.0.5 32+ bit from this page, the link that I have chosen is given below.

[debian-6.0.5-i386-DVD-1.iso.torrent]("http://cdimage.debian.org/debian-cd/6.0.5/i386/bt-dvd/debian-6.0.5-i386-DVD-1.iso.torrent")    

[http://cdimage.debian.org/debian-cd/6.0.5/i386/bt-dvd/](http://cdimage.debian.org/debian-cd/6.0.5/i386/bt-dvd/) During installation the installer could not find my network drivers and I could not even select one for my pc from a long list either. Here is my motherboard model.
[B]
                GA-G41MT-S2 [/B]

[http://uk.gigabyte.com/products/product-page.aspx?pid=4082#ov](http://uk.gigabyte.com/products/product-page.aspx?pid=4082#ov)

Can you please help me install my network card drivers in Debian? While other distros have successfully detected my network card such as Fedora 16, Ubuntu 12.04 LTS etc.
Thanks.

---

### Post by -Robert- on 2012-06-13
I found several topics about your network card (Atheros AR8151).
[http://forums.debian.net/viewtopic.php?f=17&t=64709]("http://forums.debian.net/viewtopic.php?f=17&t=79852")
[http://forums.debian.net/viewtopic.php?f=17&t=56171](http://forums.debian.net/viewtopic.php?f=17&t=56171)
[http://forums.debian.net/viewtopic.php?f=17&t=79852](http://forums.debian.net/viewtopic.php?f=17&t=79852)

It looks like you've got two options:
- Install the driver yourself (shouldn't be too difficult)
- Use a newer kernel (2.6.36 and newer) which supports your card

---

### Post by BBQdave on 2012-06-14
> **-Robert- said:**
> Use a newer kernel (2.6.36 and newer) which supports your card

+1

On an older notebook of mine (Dell Inspiron 1100) I had Debian 6. I used the netinstall cd and ethernet (cable) connection to the web. After the install, the system was up to date (netinstall) and would then recognise my wireless card.

On a side note: I have new hardware (Toshiba Satellite C655) with Fedora 16 Xfce. My old notebook (Dell Inspiron 1100 - 1 gig of ram) is now a spare (back up) to my production scene, and runs Fedora 16 Xfce solidly. I appreciate the rock solid stability of Debian 6, used that distro for a good while. But for up to date system and applications, F16 Xfce is great :)

---

