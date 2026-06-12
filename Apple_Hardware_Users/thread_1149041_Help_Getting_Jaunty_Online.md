---
title: "Help Getting Jaunty Online"
date: 2009-05-04
forum: Apple Hardware Users
---

### Post by harmonz on 2009-05-04
The WiFi network provided by an Apple Base Station (Airport Extreme) is recognized by a Powerbook G4 1.5 GHz internal Card with 10.4.11. It is recognized on an IBM ThinkPad running Windows XP with a NetGear USB adaptor. It is not hidden. BUT Jaunty does not find it on the same Powerbook G4 1.5 GHz.

Using the Network tool in Jaunty, and entering an IP Address of 127.0.0.1 I get a local network recognized and assume it is the Airport Extreme. But it remains hidden and no connection occurs. I have entered the correct 128 WEP encryption, as done on the IBM running Windows XP and it is online. 

Any thoughts what I am missing with the Jaunty Setup?

Thanks,

Marc

---

### Post by pxwpxw on 2009-05-04
> **harmonz said:**
> The WiFi network provided by an Apple Base Station (Airport Extreme) is recognized by a Powerbook G4 1.5 GHz internal Card with 10.4.11. It is recognized on an IBM ThinkPad running Windows XP with a NetGear USB adaptor. It is not hidden. BUT Jaunty does not find it on the same Powerbook G4 1.5 GHz.

Using the Network tool in Jaunty, and entering an IP Address of 127.0.0.1 I get a local network recognized and assume it is the Airport Extreme. But it remains hidden and no connection occurs. I have entered the correct 128 WEP encryption, as done on the IBM running Windows XP and it is online. 

Any thoughts what I am missing with the Jaunty Setup?

Thanks,

Marc

Have you installed  System/Admin/Hardware Drivers/Broadcom B43 wireles driver
- it install b43 fwcutter firmware.

---

### Post by harmonz on 2009-05-05
No I did not. 
You're saying that I need to install a wireless driver b43 fwcutter firmware in the jaunty System folder in order to use the airport card on my computer? This is standard? As anyone using a Powerbook would need to do? 
Do I download this driver from the internet or is it stored somewhere with the jaunty install?

Thanx

---

### Post by cyberdork33 on 2009-05-05
If you use the hardware drivers dialog, it should retrieve, extract, and place the firmware in the proper location.

---

### Post by stream303 on 2009-05-05
BTW, once you get your airport extreme wireless card working (System > Administration > Hardware Drivers), and allowing it to activate and automatically install the B43 firmware cutter, I've had no problems with WPA or WPA2 - you might consider switching from WEP to WPA.

But first a catch-22:  for the most part, the easiest way to do this is to first be attached to the internet via an ethernet cable.  Once you have activated the proprietary firmware cutter as detailed above, you can disconnect your ethernet cable for good. :)

A note to others that may not have an Airport Extreme card - 9.04 has greatly improved wireless support, especially with Atheros wireless chipsets and the new Network Manager.  I have successfully run a Belkin F5D5070 and a Netgear WG111v2 usb-stick on my G5 iMac without any problems or manual text-file configurations.

---

### Post by harmonz on 2009-05-07
I have run System > Administration > Network drivers and saw B43 Firmware Cutter and clicked to install. Which produced a window with a progress bar that quickly went to a little square window with a large Red Dot and a vertical slash. It will not install. Is there more to consider to setup. I am on running Ubuntu off an ext. HD trying to recognize the Airport Card on the Powerbook 1.5 GHz. 

Your help is appreciated,

Thanks

---

### Post by pxwpxw on 2009-05-07
> **harmonz said:**
> I have run System > Administration > Network drivers and saw B43 Firmware Cutter and clicked to install. Which produced a window with a progress bar that quickly went to a little square window with a large Red Dot and a vertical slash. It will not install. Is there more to consider to setup. I am on running Ubuntu off an ext. HD trying to recognize the Airport Card on the Powerbook 1.5 GHz. 

Your help is appreciated,

Thanks

Do you have a wired network connection running, it needs that to get the package.
Also 'System > Administration > Network drivers` sounds wrong for Ubuntu desktop, but you may be using something else.

---

