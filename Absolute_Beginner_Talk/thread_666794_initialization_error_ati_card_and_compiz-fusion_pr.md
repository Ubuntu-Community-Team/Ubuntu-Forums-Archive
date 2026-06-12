---
title: "initialization error ati card and compiz-fusion problems"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Phil420 on 2008-01-13
When i try to open the catalyst control center, from my ati radeon x1650 pro card, i get this message 
[IMG]http://i263.photobucket.com/albums/ii146/420phil/Screenshot-Initializationerror.png[/IMG]
as you can see the text is cut on the right side... i don't know if my screen resolution is involved but i can't set it to the one i need, it's too big.. but anyways i need to make compiz work, but every time i run this in the terminal : compiz --replace
all my screen becomes blank and i can't see any thing.. compiz worked before but i tried to install some plugins from another how-to and it went bad. any 1 have an idea of what to do??
Thanks!

---

### Post by nikoPSK on 2008-01-13
Possibly xorg got messed up? Do this please:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

### Post by Phil420 on 2008-01-13
i did what u said and it did this
```

phil@Phil-Desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for phil:
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080113185533
phil@Phil-Desktop:~$ 

```
any idea?

---

### Post by nikoPSK on 2008-01-13
> **Phil420 said:**
> i did what u said and it did this
```

phil@Phil-Desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for phil:
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080113185533
phil@Phil-Desktop:~$ 

```any idea?

I don't really know what dialog frontend is about. Sorry...:(

Best,
nikoPSK

---

### Post by nikoPSK on 2008-01-13
maybe try:

```
sudo su
```

then 

```
dpkg-reconfigure -phigh xserver-xorg
```

---

