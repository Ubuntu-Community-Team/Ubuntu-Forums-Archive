---
title: "can bsd be succensfully installed on asus eeepc"
date: 2009-02-10
forum: BSD
---

### Post by cmay on 2009-02-10
hi.
i am getting really tired of using crunch-bang on my asus eeepc and i use it mostly for skype but i use it almost everyday for that. it is a model 701sd , i wonder if i could use a bsd variant for this purpose or else i would have to use debian lenny on it and spend very much time configure it so it does the only few things it is actually in use for and not anything else than this. i already have debian lenny ,crunch bang ,ubuntu and studio64 installed on my other (older) computers so i am getting a bit bored by using linux only at the time. 

can bsd be a good try out for such a project. 

thanks for the time.

---

### Post by cardinals_fan on 2009-02-10
[http://en.wikipedia.org/wiki/ASUS_Eee_PC#Compatible_operating_systems](http://en.wikipedia.org/wiki/ASUS_Eee_PC#Compatible_operating_systems)

---

### Post by cmay on 2009-02-10
thanks a lot. i never seen this before but i bookmarked it. 

this means i could end up using either solaris or bsd on my asus what ever the skype is most easy to set up. i have only tried linux distributions made for the eeepc on it  but i like the crunch bang best out of all the linux eepc distributions i tried .

---

### Post by cardinals_fan on 2009-02-10
Skype isn't going to happen on Solaris.  It might work through one of the BSD linux emulators.

---

### Post by cmay on 2009-02-10
deskstop bsd could then ?.

---

### Post by cardinals_fan on 2009-02-10
> **cmay said:**
> deskstop bsd could then ?.
An up-to-date Skype version is in the FreeBSD ports collection through Linux emulation.  NetBSD has an old version.

To answer your question more directly, probably yes.  I don't know how well it works, but I have no reason to suspect problems.

---

### Post by cmay on 2009-02-10
i am going to try this out. i have a desktop bsd cd somewhere i used once but i had it installed only for a short while in the pc i use for testing. 
 i am going to just use that.
 
thanks .

---

### Post by Daisuke_Aramaki on 2009-02-12
skype works fine here using linux emulation on my freebsd laptop

---

### Post by Daisuke_Aramaki on 2009-02-12
By the way the following is a report of a user named trev, trying freebsd on his 701 Eee pc.

> Eee PC 701 (2G memory, 4G SSD, 16G SDHC)

* CPU: Intel Celeron M 353 900MHz processor (underclocked to 630.07-MHz 686-class CPU)
* WLAN: Atheros 5424/2424 - ath(4)
* Ethernet: Attansic L2 FastEthernet - ae(4)
* Function Keys: acpi_asus(4), acpi_video(4)
* Touchpad: synaptics (X11)
* Hardware monitoring: eeemon(4)
* Audio: Realtek ALC6628 Hi-Definition Audio - snd_hda(4)
* WebCam: unsupported

Works brilliantly except that running FreeBSD off the 16G SDHC card means that I cannot put it to sleep and wake it up again, because outting it to sleep disconnects power from the USB bus which in turn disconnects the SDHC card reader and FreeBSD panics on awalening because it cannot find its file system.

(I need XP on the SSD for my wife's photography cataloguing software).

---

