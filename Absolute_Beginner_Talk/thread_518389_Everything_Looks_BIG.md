---
title: "Everything Looks BIG"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-08-05
I like Ubuntu, but everything looks large
[click here]("http://i19.tinypic.com/623aold")
I think it has to do with my resolution. How can I fix this. 

LSPCI:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)


```

---

### Post by jojohippo on 2007-08-05
I agree... my resolution is set the same as it is in windows but everything still seems bigger in ubuntu (and the fonts seem wider). I'd love to know how to fix this

---

### Post by tdrusk on 2007-08-05
> **jojohippo said:**
> I agree... my resolution is set the same as it is in windows but everything still seems bigger in ubuntu (and the fonts seem wider). I'd love to know how to fix this

Oh good. I'm glad I'm not the only person.

---

### Post by coront on 2007-08-05
same here. I would love to have smaller menus and panels so the actual browsing screen is bigger. Everything is bigger in ubuntu

---

### Post by kevinmedina on 2007-08-05
go to system -> administration -> synaptic -> then search for "915resolution"

Install that tool, it should fix that problem

Also, this helped me: go back to synaptic and install "x-server-xorg-video-intel" this updates your video driver to the latest intel driver applicable to that generation

also, in terminal type

[PHP]sudo gedit /etc/X11/xorg.conf / [PHP]

and post the file

---

### Post by tdrusk on 2007-08-05
After searching around some more, I found this.

Go to System>Preferences>Fonts

Change all the sizes to 9. It helps a bit.

---

### Post by por100pre1 on 2007-08-05
> **fuzzyhair said:**
> After searching around some more, I found this.

Go to System>Preferences>Fonts

Change all the sizes to 9. It helps a bit.

I changed the font to Free Sans font, give it a try... :)

---

### Post by tdrusk on 2007-08-05
> **por100pre1 said:**
> I changed the font to Free Sans font, give it a try... :)

Very nice very nice.

Window bottoms are still kind of big.
[Click This]("http://i17.tinypic.com/6bk1jc8.jpg")

---

### Post by por100pre1 on 2007-08-05
> **fuzzyhair said:**
> Very nice very nice.

Window bottoms are still kind of big.
[Click This]("http://i17.tinypic.com/6bk1jc8.jpg")

Another workaround can be to try another theme...

---

### Post by tdrusk on 2007-08-05
> **por100pre1 said:**
> Another workaround can be to try another theme...

I really like the Ubuntu Human Theme. Anything like it?

---

### Post by ticklecricket on 2007-08-05
Just sit farther away from your monitor.

---

### Post by Hobo Joe on 2007-08-05
[www.gnome-look.org](www.gnome-look.org)

That has all the themes  you could ever want. I'm sure it has variants on the human theme. You might find some other things you like there too. :D

---

### Post by por100pre1 on 2007-08-05
> **ticklecricket said:**
> Just sit farther away from your monitor.

Please, if you don't have an useful answer, don't give any at all.

Fuzzyhair, please check [http://gnome-look.org/]("http://gnome-look.org/") and search something like "ubuntu human". You can also install Art-Manager:

```
sudo apt-get install gnome-art
```

and download some themes. Then go to the themes menu and try some tweaking. Hope this helps... :)

---

### Post by tdrusk on 2007-08-06
Thanks everybody!

---

