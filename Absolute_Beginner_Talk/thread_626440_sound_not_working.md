---
title: "sound not working"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by arjayes on 2007-11-29
Please help . My volume control icon has a cross over it . like its in mute . And when i try to open it it shows a dialog box saying 
```

No volume control GStreamer plugins and/or devices found

```
It was working fine till now .

---

### Post by natehatewindows on 2007-11-29
soudns like you dont have a sound card installed. i recently got this same error in mandriva. please post output of 

```
lspci
```

---

### Post by arjayes on 2007-11-29
```

[02:17 PM]:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 11)
07:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:01.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```
I hope u have taken into consideration the fact that it used to work fine . And I on't know what exactly caused it to stop working .

---

### Post by natehatewindows on 2007-11-29
you have the same stuff as me. i dont have sound in gusty. when it stopped working in manrdiva like this it was becase i installed a modem driver. have you installed anything havng to do with sound? have you tried to reboot?

---

### Post by arjayes on 2007-11-29
Well I did install xine-ui 
besides that I did have some problem with user permissions ,
I had by mistake removed my only administrator account from the administrator group.
It was when I rebooted after setting this right that this happened .
I didn't think this had anything to do with the sound not working .

---

### Post by natehatewindows on 2007-11-29
my best advice at this point is try to redo whatever you did. i guess try to set it wrong again and see if that fixes it. also maybe try to remove xine and see if that wors..i would do that first. what kind of computer do you have?

---

### Post by arjayes on 2007-11-29
It still doesn't work I tried uninstalling xine. no difference 
Somebody please help

---

### Post by arjayes on 2007-11-29
Somebody . pls help this is really important .

---

