---
title: "Wireless Internet Woesabd"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Henry Rayker on 2006-03-10
So I went out and bought a wireless card for my new laptop. I figured, I've never had a laptop before, and I've never had linux before, so I'll start here...I feel like that was a bad idea now...

Here's what's up:

I bought an Airlink 802.11g MIMO XR Cardbus Adapter. After a little research, I found that it's the rt2600 chipset (sometimes referred to as rt61) by ralink technology. I followed instructions to compile the driver  myself from the open source that was released...but I got to a step in the process that required the command

sudo make all

this just didn't work at all. I was told that make is not a valid command or somesuch.

I turned to another alternative...I decided I would try ndiswrapper. I got the driver to install...WOOOO!!!! but then... when I do

ndiswrapper -l

I get this:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Installed ndis drivers:
rt61    driver present

Those perl warnings kinda worry me, but they're just warnings...but the page I was reading said that I should not only get the "driver present" message, but additionally, I should get the "hardware present" message...which I don't...When I plug the card in, the "POWER" LED should light up, but it doesn't...however, in Windows, it does. I'm starting to think perhaps that whole port is unrecognized, but when I look at my hardware configuration, my SmartCardBus MultiMediaBay is present...do I need to mount the device?

---

### Post by Sendervictorius on 2006-03-10
You need to install the build tools onto your computer to get make working.

Go into synaptic and install build-essential

---

### Post by AtinLango on 2006-03-10
[QUOTE=Sendervictorius]You need to install the build tools onto your computer to get make working.

Go into synaptic and install build-essential[/QUOTE]

BTW, for the 3 weeks I have used Linux (Ubuntu), I thought build-essential is NOT installed by default in Ubuntu, until I was told it is installed by default. Which is which?

---

### Post by Sendervictorius on 2006-03-10
No its not installed by default. You can see by going into synaptic. Build-essential is not a package, its a package list.

---

### Post by Henry Rayker on 2006-03-10
I already had build-essential installed...so that's not the problem, I'm afraid...

When I do lspci, I don't actually SEE the hardware...so I'm thinking maybe it's a driver for them cardbus?

0000:00:09.0  Cardbus bridge: 02 Micro, Inc. 0z711M1 SmardCardBus MultiMediaBay Controller (rev 20)

0000:00:09.1  Cardbus bridge: 02 Micro, Inc. 0z711M1 SmardCardBus MultiMediaBay Controller (rev 20)

those are the entries corresponding to my Cardbus...but I don't know where to go from there...

---

### Post by Henry Rayker on 2006-03-10
bump

no other ideas?

when i do **cardctl status** I get a message saying that there is no card in my slot...has anyone ever had this problem before?

---

### Post by Henry Rayker on 2006-03-11
I completely uninstalled ubuntu (I was using the amd64 version) and installed the regular x86 version, hoping this would work, but this is what these commands give...

**$ lspci**
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1 SmartCardBus MultiMediaBay Controller (rev 20)
0000:00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1 SmartCardBus MultiMediaBay Controller (rev 20)
0000:00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx MultiMediaBay Accelerator0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP

**$ cardctl status**
Socket 0:
  no card
Socket 1:
  no card

This is with no attempt at trying to install the driver. I've basically installed, set up a couple preferences (just changed the name of my mounted drives), plugged in the card and performed these commands. I wanted to make sure all was right with the hardware first. I guess my problem has changed just a little bit. Is there anything fishy about these reading?

---

### Post by dragonfyre13 on 2006-06-01
Oh god. Try just a simple "sudo -s && ./configure && make && make install"

See if that works.

P.S. the oh god is because noone suggested this before.

And I really reccomend upgrading to dapper. I have this specific card working out of the box on it, and it is great.

---

