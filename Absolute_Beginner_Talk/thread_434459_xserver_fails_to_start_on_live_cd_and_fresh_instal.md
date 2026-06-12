---
title: "xserver fails to start on live cd and fresh install (on fiesty regular &amp; alternative)"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by JimmyHopkins on 2007-05-06
Before we start, I have a :

Emachine
60 gigs HD
2700 mghz Celeron D
760 megs of sd RAM
256 mb geforce 5600 fx video card installed in an available PCI slot
A working ethernet connection
My Computer came with a 64 meg agp intell graphics card, and it is connected directly onto the motherboard

Regular live cds won't boot x. So I tried the alternative cd, which installed ubuntu on my computer. However, when I boot up, x still won't start. I've tried:

apt-get install ubuntu-desktop
apt-get install xserver-xorg-video-intel
apt-get install gnome-desktop
apt-get install kde-desktop
apt-get install xserver-xorg-core

the terminal works of course, and I did all of the above commands with sudo -su.


Thanks in advance.

and even uninstalled xserver and re-installed it. X simply won't boot up.

---

### Post by JimmyHopkins on 2007-05-06
bump

---

### Post by taurus on 2007-05-06
What happens when you run this command from a prompt after you've logged in?

```
startx
```

---

### Post by JimmyHopkins on 2007-05-06
Xserver failed to start and gave the error window.

---

### Post by taurus on 2007-05-06
Then you need to reconfigure your X again.

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by tgalati4 on 2007-05-06
Post 

/var/log/Xorg.0.log

If the Live CD didn't work, then chances are the install will have the same problem.  I admire your persistance, though.

Take out the GeForce card and set the BIOS to use the on-board graphics card.  First get a working system then you can add the graphics card back in. 

Linux is not a Plug-and-Play operating system, so turn that OFF in the BIOS.

Let us know if you can a graphical desktop with the on-board graphics.

You will eventually want dual-monitor, but let's get one thing working at a time.

---

