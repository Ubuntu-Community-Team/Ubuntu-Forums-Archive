---
title: "Changing video card"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by BillGod on 2007-03-18
I am running into a strange problem where anything that requires any amount of GPU my system locks for 45 seconds at a time.  I can run normal apps all day but as soon as I launch ut2004 or WOW It starts to lock.  This worked 2 weeks ago?  Any way...  I wanted to see if it is my video card.  Nvidia 4200.  The only other card I have is the built in intel card.  I cannot seem to figure out how to install the video driver for it.  If I run dpkg-reconfigure xserver-xorg I have no option for an intel gpu.  anyone know how to get this working?  or any other Ideas as to why its locking all of a sudden?

This is my edgy box.. btw my feisty box works beautifully

---

### Post by taurus on 2007-03-18
Just edit your /etc/X11/xorg.conf and use "i810" as a Driver for your onboard Intel graphic controller.

```
sudo nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o and <Ctrl>x to save and exit.

---

### Post by gradedcheese on 2007-03-18
edit: the following maybe applies if what is said above doesn't work...

I think that what's going on here is that onboard Intel cards usually have to be be switched on in the BIOS (they disable when an AGP card like your Nvidia is detected).  The OS then doesn't even see the Intel card.  Reboot and get into the BIOS and find the setting for that, change the primary video to the onboard card.  Once Ubuntu boots, it should detect the change and reconfigure, otherwise get to a shell and reconfigure xorg as you did before.

---

### Post by oilchangeguy on 2007-03-18
when you installed the pci card did you modify the bios? if so go back in and re-enable onboard video.

---

