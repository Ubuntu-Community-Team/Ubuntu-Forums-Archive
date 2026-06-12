---
title: "Installing Ubuntu 6.1"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by xlinuks on 2007-02-08
Hi
I wanna install Ubuntu, but it looks like it tries to make use of the video card during installation and since it doesn't handle it correctly the screen shows weird lines all over the screen.
The question is: Is it possible to install Ubuntu 6.1 in text-mode only, if so, how?

Please help!

Additional info: OpenSuse 10.2 had same problem, not during the installation though, but when starting up the X Server, so I only install the official nVidia driver after system installation (before starting the X-Server) and I'm done. I'd like to do same with Ubuntu.

Previous distros:
What is weird that these OS (along with, for example, Solaris 10) identifies correctly my videocard (MSI GeForce 6800GS 256MB PCI-Ex) but when it starts using it - it fails.
On the other hand Mandriva PowerPack installed fine without problems, Slackware 11 worked after I chose a different driver during installation.

---

### Post by PartisanEntity on 2007-02-08
I believe the live cd version of Dapper (ubuntu 6.10) has text mode installation.

---

### Post by xlinuks on 2007-02-08
OMG you replied faster than I managed to re-read my post. Thank you, I only know that I tried Ubuntu 6.1, not sure whether it's Dapper or not, but I know that it tried using by default my videocard and failed, how do I prevent it, only by trying to install the LiveCD? thanks

---

### Post by PartisanEntity on 2007-02-08
It depends which CD version you downloaded.

In the Live CD version, when you boot from the CD, you get a menu, one option is to install or launch ubuntu another should say something like 'text mode install', this is the one you probably want.

Someone correct me if I am wrong.

---

### Post by jvc26 on 2007-02-08
6.10 is Edgy, 6.06 is Dapper. What is your gfx card?
Il

---

### Post by PartisanEntity on 2007-02-08
> **Illuvator said:**
> 6.10 is Edgy, 6.06 is Dapper. What is your gfx card?
Il

Duh! sorry, I wasn't thinking :)

---

### Post by jvc26 on 2007-02-08
To install in text mode you have to download the alternate install cd from the Ubuntu site, burn it to cd and then boot with that. Unless you have the live DVD version which has both the text installer and live cd in one (If I remember rightly, dont quote me on that one ;))
Il

---

### Post by xlinuks on 2007-02-08
I found the 'alternate' distro at
[ftp://ftp.fu-berlin.de/linux/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso)
I hope this one has the 'text-mode' option, I'm gonna download and check it.
Thank you all for your time!

---

### Post by had3z on 2007-02-09
it is a problem with your video card. the standard drivers won't work. ubuntu loads just fine.
search on the forums for "6800gs" and you will find your answer. it's about editing xorg.config and changing the line that has "nv" into "vesa"

---

