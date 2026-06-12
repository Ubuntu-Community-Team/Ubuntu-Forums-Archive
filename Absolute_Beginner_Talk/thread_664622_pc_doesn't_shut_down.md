---
title: "pc doesn't shut down"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by erikw on 2008-01-11
I installed 7.10 on my Acer Extensa 5620 but when I close Ubuntu I got the following message on a black screen;
-networkmanager: <warn> nm_signal_hadler(): caught signal 15, shutting down normally
-networkmanager: <info> caught termination signal
-networkmanager: <debug> [1200057705.773186] nm_print_open_socks():open socket list
-networkmanager: <debug> [1200057705.773282] nm_print_open_socks():open sockets list done
-networkmanager: <info> deactivating device eth0
-networkmanager: <info> deactivating device eth1

After that I get a blinking cursor and I need to shut off power manually.

I allready tried this with the same result, doesn't help!!

> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

---

### Post by nikoPSK on 2008-01-11
does this shut it down? 
```

sudo shutdown -h now
```

---

### Post by erikw on 2008-01-12
Brings me after the screen with the mentioned text to a screen with UBUNTU and then after a few seconds a black screen with a blinking cursor in the left hand top.
But NO power of for the notebook!

---

### Post by erikw on 2008-01-12
Does anybody has an idea to solve this problem??
Thanks in advance.

---

### Post by philinux on 2008-01-12
Check the link below for known bugs. Scroll down to the entry for shutdown hanging.

---

### Post by nikoPSK on 2008-01-12
> **erikw said:**
> Brings me after the screen with the mentioned text to a screen with UBUNTU and then after a few seconds a black screen with a blinking cursor in the left hand top.
But NO power of for the notebook!

so it's not the applet malfunctioning... :(

---

