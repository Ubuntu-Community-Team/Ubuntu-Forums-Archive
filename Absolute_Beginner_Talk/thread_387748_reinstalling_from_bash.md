---
title: "reinstalling from bash"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Varz on 2007-03-18
Hi,
I've got a laptop with no cdrom or floppy drive which won't boot from usb, it did have windows xp already installed so I tried to install kubuntu via this method: [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

It seemed to go through the installation alright but now I'm only left with a shell.  Is there a command to reconfigure the whole installation from bash?  Some command to get the installer up again?

---

### Post by raja on 2007-03-18
Do you mean a terminal comes up and you are able to log in, but are not able to see a graphical desktop ? In that case, can you try ```
startx
``` and see if the desktop comes up? Otherwise you can install Kubuntu with ```
sudo aptitude install kubuntu-desktop
```

---

### Post by annda on 2007-03-18
or ubuntu with gnome (less resources required)
sudo aptitude install ubuntu-desktop
sudo aptitude install gdm

---

### Post by Varz on 2007-03-18
I installed kdm but I don't know the name of the theme package so it starts as just a blue background with a terminal in the corner.

I tried installing kubuntu-desktop but I get an error saying not enough space in /var/cache/apt/archives.  I made a separate partition for /var but it was only small (like 500mb), is there a way to change were apt get stores the files it downloads?

---

### Post by Varz on 2007-03-18
Dammit its fked now i accident deleted the root partition.  I don't know how the hell I'm going to get anything working on this now I tried to pxe boot before but for some reason it wasn't working.  I kept getting a message "unexpected request by client" when trying to boot.

DAMMIT!!!!!111:evil:

---

### Post by Varz on 2007-03-19
WIIIIIIIIIIIIIIII!!!!!!!!1111111

pxe boot worked, note to anyone trying to pxe boot from windows, if tftpd32 doesn't work try pxe booting from linux.

Thanks anyway.

---

