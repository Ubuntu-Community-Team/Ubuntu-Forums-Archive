---
title: "[SOLVED] Gutsy 64 bit  and Bluetooth"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-10-26
When I right click the Bluetooth Analyzer icon in the tray and select 'Browse Device' and then select my phone, I get this error message
```
"obex://[00:16:b3:46:d4:71]" is not a valid location.
Please check the spelling and try again.
```

---

### Post by Inxsible on 2007-10-26
I tried this too :
```
inxsible@inxsible:~$ sudo hcitool scan
Scanning ...
        00:16:B3:46:D4:71       W810i
inxsible@inxsible:~$ sudo hidd --connect 00:16:B3:46:D4:71
Can't create HID control channel: Connection timed out
inxsible@inxsible:~$ 
```

---

### Post by Doc on 2007-10-26
I'm getting the same error, except instead of a time out error I get 
```
Can't get device information: Host is down
```
I've tried all the possible BT Manager settings...it worked fine in feisty with the same hardware, I don't understand it.

---

### Post by insane_alien on 2007-10-26
my gutsy 64-bit isn't having any problems with bluetooth. what does your lsusb(or lspci if it is built in) have to say about the device.

---

### Post by Inxsible on 2007-10-26
Here's my lspci
```
inxsible@inxsible:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
inxsible@inxsible:~$ 

```

---

### Post by Doc on 2007-10-28
The solution for me was to uninstall the default bluez-gnome package (requires a reboot to make the applet go away btw) and install the blueman package available at 

[http://blueman.tuxfamily.org/]("http://blueman.tuxfamily.org/")

Works perfectly for file transfers, which is all I need.

---

### Post by Inxsible on 2007-10-29
> **Doc said:**
> The solution for me was to uninstall the default bluez-gnome package (requires a reboot to make the applet go away btw) and install the blueman package available at 

[http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/)

Works perfectly for file transfers, which is all I need.Instead of adding yet another deb and keeping track of its update, I am gonna go with Bluetooth File Sharing app, found in the Applications --> add/Remove. This is what I used in Feisty too and it worked great. Also I don't know if blueman supports a 64 bit architecture. so I might have to compile from source :( which is easy enough, but its just that I want to keep that to a minimum.

---

### Post by walmis on 2007-11-28
Blueman now has it's own repository, and amd64 packages are available too

---

