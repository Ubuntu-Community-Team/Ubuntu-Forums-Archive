---
title: "Can my Wifi light not be flashing all the time?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-04-28
Whenever I have Wifi enabled, my Wifi light on my laptop goes nuts.  is there a way to just make it stay on solid or even turn off?  I'd prefer solid if it's possible.  Thanks!

---

### Post by Bachstelze on 2007-04-28
What kind of WiFi card is it ?

---

### Post by gohanssjn on 2007-04-28
It's an Intel 3495 A/B/G in a Dell XPS-1210.  So it's the light on the top of the keyboard area.

---

### Post by Bachstelze on 2007-04-28
Seems you can only turn the LED "always off", not "always on". Could you please paste the output of this command ?

```
lspci
```

---

### Post by gohanssjn on 2007-04-28
> **HymnToLife said:**
> Seems you can only turn the LED "always off", not "always on". Could you please paste the output of this command ?

```
lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by Bachstelze on 2007-04-28
So, as you could have found out by reading the README, the LED can be controlled through the /sys/bus/pci/devices/0000\:0c\:00.0/led sysfs helper file. To disable it, just do :

```
echo "0" | sudo tee /sys/bus/pci/devices/0000\:0c\:00.0/led
```

---

### Post by nickpaton on 2007-04-28
You could always put a piece of tape over it   :lolflag:

---

### Post by Bachstelze on 2007-04-28
That's what I do sometimes 'cause I can't control the power led of my lappy :p

---

### Post by NilsE on 2007-04-28
Is it actually connected to a wireless router?  

Mine only blinks when it is searching and stays on steady when it is connected.

By the way, Dell Latitude D620 with the same WiFi adapter.

---

### Post by Rebel Dragon on 2007-05-28
How do I make this change permanent? 

(I'm actually trying to set "led=1")

The command works, but a reboot changes it back.

---

### Post by wheresraz on 2008-02-22
hey, i am completely new to ubuntu so not sure if this was what worked for me. but i'm pretty sure that my flashing light issue was fixed when installed the "network-manager" package.  when i connect to wireless my light is now solid and on.   you have to be in roaming mode and select a network. 

also, i have the same laptop as you. dell m1210 so hopefully that helps you out.

---

