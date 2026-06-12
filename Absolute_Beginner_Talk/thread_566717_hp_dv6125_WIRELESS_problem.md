---
title: "hp dv6125 WIRELESS problem"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by chraej on 2007-10-03
just installed ubuntu onto my laptop (dv6125) and cannot get the wireless to recognize...there is a switch that when on should be illuminated blue but instead it stays red when in ubuntu and the connections list doesnt recognize any wifi connections/card, any help?

---

### Post by jfinkels on 2007-10-04
First you need to determine your wireless network card. To do that, type in the terminal ("Applications > Accessories > Terminal"):```
sudo lspci -v
``` and type your password when prompted. Look for a section that shows "Ethernet controller", and there you'll have your make and model of wireless network card (there will be one for each network interface card you have, so you may have one for your wired connection, and one for your wireless connection). If you can't figure it out, just post the output of the command here. Once you determine your wireless network card, you may need to download a driver for it. But that's the second step.

---

### Post by chraej on 2007-10-05
network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PC i card (rev 01)
Subsystem: Hewlett-Packard Company Unknown device 1363
Flags: bus master, fast devsel, latency 0, IRQ 255
Memory at b3200000 (32-bit,non prefetchable) [size=16k]
Capabilities: [40] Power Management version 2
Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0
Enable-
Capabilities: [d0] Express Legacy Endpoint IRQ 0

* now that i've gotten compiz fusion installed my normal terminal has gone white (so i'm using xterm) and my borders have dissapeared, any help w/ these would be welcome also ;)

---

### Post by jfinkels on 2007-10-05
I believe (from some brief searching based on your network controller name) that since you have a Broadcom card, you require the bcm43xx driver, which must be installed on top of ndiswrapper (a layer that allows installation of Windows drivers on top of Linux software).
See here for an introduction on how to install the bcm43xx driver: [http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html) 

Let us know how it goes.

---

### Post by chraej on 2007-10-06
everything goes well untill i use $sudo ./ndiswrapper_setup where i get the
Pausing for 10 seconds - please read the message.
./ndiswrapper_setup: 1: Syntax error: Unterminated quoted string

---

### Post by jfinkels on 2007-10-07
> **chraej said:**
> everything goes well untill i use $sudo ./ndiswrapper_setup where i get the
Pausing for 10 seconds - please read the message.
./ndiswrapper_setup: 1: Syntax error: Unterminated quoted string

Err, it seems that the site to which I directed you asks you to use an old script, so forget that. My apologies. Here's a potentially better method (you can find several methods for getting the bcm43xx firmware at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset) ):

1. Open your list of software repositories by typing the following in the terminal:```
sudo gedit /etc/apt/sources.list
```
2. Add the 'cafuego' software repository by adding the following two lines to the bottom of the file:```
deb http://ubuntu.cafuego.net feisty-cafuego bcm43xx
deb-src http://ubuntu.cafuego.net feisty-cafuego bcm43xx

```
3. Save the file and close gedit.
4. Type the following in the terminal to add this repository's public key to your list of trusted keys (for authentication purposes):```
wget http://debian.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
``` 
5. Type the following in the terminal:```
sudo aptitude update
```
6. Install the firmware:```
sudo aptitude install bcm43xx-firmware
```

Let me know how this goes. If it doesn't work, you might want to try some of the other methods listed there, or search around on the forums for ways people have installed the bcm43xx firmware.

---

### Post by chraej on 2007-10-08
> Setting up bcm43xx-firmware (1.3-1ubuntu2) ...
Note that you need to DISABLE ndiswrapper and wifi-radar for this driver
to work properly! You can do this by removing the ndiswrapper driver.
Use `sudo ndiswrapper -l' to identify the driver.
Then run `sudo ndiswrapper -e <driver>' to remove it. You may also need
to remove the file /etc/modprobe.d/ndiswrapper


does this mean i cannot use ndiswrapper at the same tme?

---

### Post by chraej on 2007-10-09
disregard that! problem solved, my connection now recognizes the wireless networks, much thanks!

---

