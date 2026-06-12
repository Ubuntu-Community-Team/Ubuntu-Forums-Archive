---
title: "Nvidia drivers for iMac (Ubuntu 13.10)"
date: 2013-11-05
forum: Apple Hardware Users
---

### Post by eugene.balkind on 2013-11-05
Hi all!

I have just got a new iMac 14.3 with 21.5' display. It has Intel i7 processor and NVIDIA GeForce GT750M graphics card with GPU (Device ID: 0x00fe9). I have installed Ubuntu 13.10 on it (dual boot with refit). Everything works fine apart from graphics. It is clear that graphics' not accelerated. I have tried to

1) Install nvidia drivers from the repository.
2) Download nvidia drivers and install them manually.
3) Follow instructions on [http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/](http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/) .
4) Follow instructions on [http://dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://dedoimedo.com/computers/ubuntu-ringtail-nvidia.html) .
5) Follow instructions on [http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver](http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver) .
6) Install bumblebee.
7) Play around with xorg.conf file.
8) Blacklist nouveau.

As you may guess, nothing worked. The weirdest thing is, that when I boot from a LiveCD, it picks up screen resolution and all the rest correctly, though when I install the system to my Hard Drive it clearly does not have proper drivers. Does anyone have any suggestion what to do?

Regards,
Eugene.

---

### Post by mpbishop on 2013-11-07
Did you try the Mac-specific Ubuntu installer disc?

--> [http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-amd64+mac.iso](http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-amd64+mac.iso)

Not sure if this will solve your problem but it could be a starting point. Also, did you select to install proprietary add-ons as well when you did your install?

---

### Post by eugene.balkind on 2013-11-07
Thank you for your reply! Yes, I use the Mac-specific installer. Which add-ons are you speaking about?

---

### Post by mpbishop on 2013-11-08
Usually there is an option during installation (you can also do it post-installation through Software Center) called "restricted add-ons" which I understand include some non-open-source software and drivers. I installed these when I put Ubuntu 13.10 on my Macbook Pro, and everything worked flawlessly. But your iMac has a totally different chipset, so this may not solve it for you. I wish I could be of more help!

---

### Post by eugene.balkind on 2013-11-10
Yes, I always install them on a fresh system.

---

