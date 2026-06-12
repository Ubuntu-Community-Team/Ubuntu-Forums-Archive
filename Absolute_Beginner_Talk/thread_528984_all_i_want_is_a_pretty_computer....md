---
title: "all i want is a pretty computer..."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by cmlewin on 2007-08-18
I'm having the most awful time trying to get desktop effects, or compiz, or beryl running on my computer as all i want in this world is a dock (AWN)... but i can't seem to have a decent one without any of that software...

i tried to install compiz... but all i got was windows that couldn't move with no borders.. and i tried a bunch of different proposed fixes but i couldn't get it working

i can't install beryl b/c i can't get direct rendering to work for the mobility radeon m6 ly tutorial as that is what seemingly i have as my video card... just made it so i couldn't get anything except terminal so i reinstalled ubuntu as i seemed to have no other choice

"desktop effects" only gives me a white screen and my mouse... nothing else...

i'm not even sure what video card i have and maybe the driver is the problem... i dunno, i'm just confused

i'm running the latest feisty on an all stock sony vaio pcg-z1ra... is it possible to get any of these working?

---

### Post by colo on 2007-08-18
Please, open a shell, run the command `sudo lspci` in it, and paste its output in here. This should make it easier for us to help you tracking down the problem.

---

### Post by cmlewin on 2007-08-18
> **colo said:**
> Please, open a shell, run the command `sudo lspci` in it, and paste its output in here. This should make it easier for us to help you tracking down the problem.

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

### Post by cmlewin on 2007-08-18
thanks

---

### Post by Kitsun on 2007-08-18
Lets set it out like this.

You want to run Beryl, however problems occur.

You claimed that you cant get direct rendering to work, focus on that first than continue.

Problems and fixes for video display chipsets are widely documented, I suggest doing a google or a forum search and find a nice howto on installing your graphics drivers.

---

### Post by Jimmyfj on 2007-08-18
This may sound silly but I have a friend who owns a laptop with a ATI Radeon mobility graphics card, and the ONLY way he can get Beryl running on his laptop is by deactivating the restricted driver. Silly, but it works that way on his system.

---

### Post by SunnyRabbiera on 2007-08-18
just remember that beryl/ compiz and compiz fusion are still developing apps, sometimes its better to have stability then flashy eye candy.

---

### Post by cmlewin on 2007-08-19
well is there a simple stable dock that looks presentable? as that's all i'm really looking for

---

### Post by cmlewin on 2007-08-19
> **Kitsun said:**
> Lets set it out like this.

You want to run Beryl, however problems occur.

You claimed that you cant get direct rendering to work, focus on that first than continue.

Problems and fixes for video display chipsets are widely documented, I suggest doing a google or a forum search and find a nice howto on installing your graphics drivers.

yeah i tried to do that but i can't really find anything specific to my comp and i don't know what else to do...

---

### Post by RomeReactor on 2007-08-19
Hi. You can try installing gdesklets; look for it in Synaptic, or to install from the terminal:
```
sudo apt-get install gdesklets
```
after it finishes installing, you'll find it in "Applications->Accessories->Gdesklets". Look at the options it shows you to start the dock.

---

