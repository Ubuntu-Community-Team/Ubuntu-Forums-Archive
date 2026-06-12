---
title: "[SOLVED] Toshiba Satellite A105-S4164 wifi problem"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Helven Ink on 2008-01-21
I'm still struggling and haven't had much help so far... All I've got are the results from an lspci command

Hello, I'm about as green and unroasted as a linux user can get. I haven't tried to run Linux, since it fried my old Cyrix 166 about 10 years ago. :p
Now I'm trying Ubuntu Frisky Fawn on my Toshiba Satellite A105-S4164, and I can't get the wifi to work.
It shows the available networks, but when I punch in the WEP key it doesn't login. It says something about the drivers being restricted on account of them being proprietary and I spent some time looking for drivers on the net, but there isn't anything for my specific model of S4164. I don't know enough about... anything really to try and find something for it. I just know it doesn't work.
Also, the sound is *REALLY, really* quiet... I don't know what the deal with that is either.
 I don't know if I need to set something up, or find new drivers.

If someone could point me to some good beginner's reading material, I'd appreciate that as well.

             Jon

---

### Post by wormser on 2008-01-21
Welcome to the Ubuntu community.  It will help us if you get the exact model number of the wifi card.  The following command will list your hardware.  Post the results.  Also, search the forum with the model number and you will probably find a guide.

Applications> Accessories> Terminal - I always right click it and Add to Panel

```
lspci
```

---

### Post by Helven Ink on 2008-01-21
I've upgraded my status from can't connect, to connected, but no internet... I've been reading the wifi FAQs but can't figure out where to go from here. I can't ping the router, but I don't know if that's because it's not getting there, or if the router has a diff ip address than 192.168.0.1 Does anyone know how I could find out?

---

### Post by Helven Ink on 2008-01-21
It's not a card, it's built into the laptop.

---

### Post by Helven Ink on 2008-01-21
It has a listing for ethernet:
Intel Corp. pro/100 ve network connection (rev 02)

I don't see a listing for wifi specifically though.
nevermind,  I found one
Network controller:
Intel corporation Pro/wireless 3945ABG Network Connection (rev 02)

Audio device:
Intel Corp. 82801G (ICH7 family) High definition Audio controller (rev 02)

I'd really like to fix the audio also... It's just so quiet... I can hardly hear anything with the volume turned all the way up...

---

### Post by wormser on 2008-01-21
> **Helven Ink said:**
> It has a listing for ethernet:
Intel Corp. pro/100 ve network connection (rev 02)

I don't see a listing for wifi specifically though.

Audio device:
Intel Corp. 82801G (ICH7 family) High definition Audio controller (rev 02)

I'd really like to fix the audio also... It's just so quiet... I can hardly hear anything with the volume turned all the way up...

It is a card, they are mini cards inside the laptop.

Post the full results of the command.  It will helps us.  Start a new thread for the sound issue and post the audio device details.

---

### Post by Helven Ink on 2008-01-21
did you see my update?
I found the wireless string.
I guess I could post the full results... I'll get to check and see if I can use a thumbdrive... ;)
Just a minute

---

### Post by Helven Ink on 2008-01-21
jeezus@McWheezy:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
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
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by Helven Ink on 2008-01-21
bump

---

### Post by Helven Ink on 2008-01-21
Please help, I can probably start figuring out how to fix most if not all the problems with my laptop if I can at least get online... There are probably programs with codecs I don't have that could possibly fix my sound issues... yeah... That's the ticket! ... That's really all I've run into so far, but not being able to get online makes it really difficult to do anything with it at all

---

### Post by wormser on 2008-01-21
> 05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I do not have time to help you right now but search the forums for [3945]("http://ubuntuforums.org/search.php?searchid=35069854").

---

### Post by Helven Ink on 2008-01-21
I have searched for it, and I've been reading quite alot about it, the trouble, is that I don't quite understand what I'm supposed to do. Is it all stuff I'm supposed to type into the terminal?
I'm lacking in a few of the basic concepts of linux, and don't really know where to start to to learn them.

---

### Post by wormser on 2008-01-21
> **Helven Ink said:**
> I have searched for it, and I've been reading quite alot about it, the trouble, is that I don't quite understand what I'm supposed to do. Is it all stuff I'm supposed to type into the terminal?
I'm lacking in a few of the basic concepts of linux, and don't really know where to start to to learn them.

I got some time now.  Any time you see a command use it in the terminal.  Read this [site]("http://www.psychocats.net/ubuntu/index.php") to get some of the basics down.  Your problem is not being able to connect with WEP.  When ever I have this issue I turn off the encryption and try connecting.  It removes one variable.  Try that first.  Also make sure the access point has the latest firmware.  I read a post about your card where that was the issue.

---

### Post by Helven Ink on 2008-01-21
I followed the direction on this site:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)
and it seemed to have it's desired effect... only I don't think I have the iwl3945 module... =p
I realize that it's for a later version, but my freind had been telling me that all versions of ubuntu since 6.10 have been compatible, so I figured it would work... Is there a way to get a copy of the iwl3945 module?

I don't know how to access the router where I am, it's not my network. and the standard address doesn't take me to the router interface.

---

### Post by Helven Ink on 2008-01-21
I was also reading about there being an issue with WEP versus hex keys... except in order to switch to the hex key, you have to change all the puters on the network right?

---

### Post by Helven Ink on 2008-01-21
What about this?
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)
Could this possibly fix my problem? and if so, how do I go about implementing it? I read the readme, but I don't quite follow...

---

### Post by Helven Ink on 2008-01-21
maybe I should just install gutsy gibbon... It comes with the driver I need... shouldn't take too long to d/l

---

### Post by Helven Ink on 2008-01-22
WOOOOOOOOO!
I fixed it!!! I don't know why I couldn't get it to work before, but after this particular attempt to configure the wifi properties, it suddenly worked!!!
I feel so much better now!

---

