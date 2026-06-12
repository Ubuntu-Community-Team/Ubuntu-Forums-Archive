---
title: "Wireless help plz"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by MrHoneyBunny on 2007-06-20
I have a Netgear WPNT121 wireless USB 2.0 adapter that i want to use for my freshly installed Ubuntu system but for whatever reason, Ubuntu doesn't detect this adapter.  When I go to the top right corner with the two black monitors that leads to the network setup, it only gives me a wired lan and modem option, it doesn't even see my adapter.  Is it because this adapter's not compatible with Ubuntu or do I just need to install something to get it to work?

---

### Post by Bachstelze on 2007-06-20
Open up a terminal ant type

```
sudo iwconfig
```

Do you see anything that doesn't say "no wireless extensions" ?

---

### Post by violin on 2007-06-20
i have the same problem 

it says 

lo   no wirelees extension
eth0 no wireless extension
sit0 no wireless extension

i think my wireless is sit0

---

### Post by MrHoneyBunny on 2007-06-20
Yeah, mine says 

lo no wireless extensions
eth0 no wireless extensions

---

### Post by violin on 2007-06-20
dude i wish i could help you.

---

### Post by MrHoneyBunny on 2007-06-20
Hehe, ditto.  Too bad neither of us know what we're doin :(

---

### Post by Bachstelze on 2007-06-20
OK, we'll need to install drivers for your wireless. Do

```
lsusb
```

and paste what you get.

---

### Post by violin on 2007-06-20
Bus 005 Device 003: ID 04f2:b008 Chicony Elections Co. Ltd
Bus 005 Device 003: ID 0000:0000
Bus 001 Device 004: ID 046d:c50a Logitecth, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000


here is the output

---

### Post by Bachstelze on 2007-06-20
Is your wireless adapter USB ?

---

### Post by violin on 2007-06-20
nope it come with laptop it is internal inside the laptop. And another point is it works on windows not on ubutu

---

### Post by MrHoneyBunny on 2007-06-20
Bus 002 Device 002: ID 1385:6e00
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:c018 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

---

### Post by violin on 2007-06-20
bump no answer sorry

---

### Post by Evan394 on 2007-06-20
> **HymnToLife said:**
> Open up a terminal ant type

```
sudo iwconfig
```

Do you see anything that doesn't say "no wireless extensions" ?

Hi,

Having the same problem desribed in this thread [LIST]
[*]my wireless card seems to be detected by system
[*]i can choose which network I want to join (which also indicates that there is some functionality)
[*]once i choose, I even get blue signal bars, but I still can't load internet pages ("Server not found")
[/LIST]with an Intel PRO/Wireless 2915ABG internal wireless card.   

when I enter ```
lspci -v | less
``` it shows up as the following
```
02:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Conne
ction (rev 05)
        Subsystem: Intel Corporation Unknown device 1010
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) 
Ethernet Controller (rev 42)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at d0201000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8000 [size=64]
        Capabilities: <access denied>
```

I noticed that both ethernet controller and wireless are on the same IRQ, is this a problem? the whole "access denied" thing in Capabilities ==:( (I assume)

---

### Post by violin on 2007-06-20
bump again

i stiill could not fix it.

---

### Post by Bachstelze on 2007-06-20
If it's PCI, do

```
lspci
```

(Yes, "integrated" cards are PCI, too)

---

### Post by violin on 2007-06-20
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1)
04:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8136 (rev 01)
06:04.0 CardBus bridge: Texas Instruments Unknown device 8039
06:04.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
06:04.2 Mass storage controller: Texas Instruments Unknown device 803b
06:04.3 Class 0805: Texas Instruments Unknown device 803c

```

output i dont know which one which thanks again answering

---

### Post by violin on 2007-06-20
Also i just checked system>admin>network  there are no wireless there as well.

Only two thing modem and cable no wireless. This is bugging me also my computer is Toshiba A-200 stalite.

---

### Post by Betta on 2007-06-20
Violin: are you sure the switch on your laptop for wireless is on? Sometimes they get pushed to the off position and wireless would not work then.

-Betta

---

### Post by violin on 2007-06-20
no wireless is on because i can use it on windows.

---

