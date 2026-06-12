---
title: "Controlling Brightness in Ubuntu"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by jimbo111 on 2007-02-12
Hello, 

Currently I'm running Ubuntu Edgy Eft 6.10 and kernel version 2.6.17-11-generic.  I just wanted to reduce the brightness of my screen, however the brightness controls on my laptop do not work with this OS. I've gone into Ubuntu help and it says to open Power Management and adjust the brightness from there, however the brightness setting does not exist. Would anyone know how I can adjust the brightness of my screen? At the moment I'm using a Theme (Silicon Theme) to somewhat help with the brightness, however, this is not helping too much. .......

Cheers :)

---

### Post by xyz on 2007-02-12
I'm using Dapper but I'll give it a shot anyways...maybe it is the same procedure. Let me know.

Go System > Preferences > Power Management > Set display brightness to

---

### Post by jimbo111 on 2007-02-12
thanks for the reply but when I go to the Power Management utility, the slider for brightness is not there....any reason for that or is there something I have to set to get that part displayed?   ..... :confused:

---

### Post by b9anders on 2007-02-12
Is there a way to adjust contrast and bright in xubuntu as well? Haven't found one so far.

---

### Post by orb9220 on 2007-02-12
Post your video chipset since these are dependent on having the right video driver installed for your laptop.

---

### Post by jimbo111 on 2007-02-12
well, I think doing an lspci gives the video chipset?? Not sure how to do that but here's the lspci output: 
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)

thanks for your help

---

### Post by xyz on 2007-02-12
What's your laptop's brand?
I have a Toshiba Satellite A 40 and I can also adjust brightness by running:
```
sudo echo "brightness:1" > /proc/acpi/toshiba/lcd
```
where "1" is the value to change. (up to 8, I think).
There may be a command line for yours out there somewhere.

---

### Post by occams_beard on 2007-02-12
I'm sure there's a better way, but you can use xgamma to adjust your monitor gamma.

e.g "xgamma -gamma  0.1" will decrease the brightness.

---

### Post by jimbo111 on 2007-02-23
Gents, apologies for the late reply. Managed to figure out how to control brightness on my laptop. :) 
My laptop by the way is a HP compaq nc6000. 
By installing a video driver called fglrx, I am now able to control brightness via my keyboard brightness controls (I just couldn't find how it works in the Power Management application). 
For details on installing this driver, just go to this website where it explains everything. 
Hope this helps somewhat. 

Cheers :) 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

