---
title: "Linksys wireless-g usb adapter"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by ClaytonK on 2007-01-18
i am completely new to linux. never touched it before in my life. i just installed buntu 6.10 last night. 

Computer specs:
Mobo- MSI k8ngm2
CPU-AMD Atholon 64 3000+
Memmory- 1GB Corsair XMS
Video-ATI radeon x1600
HD-300GB SATA maxtor (Windows System)
     120GB Segate (Linux system)
Sound-Creative soundblaster Live! audigy SE
Network-Linksys Wireless-G usb adapter

I need help setting up my network adapter, and cofiguring it to conect to my router.

---

### Post by zerwas on 2007-01-18
Hello ClaytonK,

Welcome to the big and free world of linux. :)

To help you we need additional information about your wlan-adapter. You can get this information in the device manager. Click on System - Administration - Device Manager.
There you can search for your adapter.

Alternatively to this process you can also open a terminal (by clicking on Applications - Accessories - Terminal) and enter the word "lsusb"
Then copy and paste the output here :).

Thank you for your help.

Greetings,
zerwas

---

### Post by Atreus12 on 2007-01-18
Welcome :) 

I have the same wireless card. There is no native linux driver so you have to run the windows driver in ndiswrapper. This is the howto I followed

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

Securing your wireless
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

-Andrew

---

### Post by ClaytonK on 2007-01-18
Ok, i ran the command lsusb from the terminal, and this is what i got. hope its what you need.

bus 002 device 002: ID 13b1:000d linksys
bus 002 device 001: ID 0000:0000
bus 001 device 001: ID 0000:0000

---

### Post by zerwas on 2007-01-19
Yes, Atreus12 was so nice to give you two links that will help you :)

Regards,
zerwas

---

