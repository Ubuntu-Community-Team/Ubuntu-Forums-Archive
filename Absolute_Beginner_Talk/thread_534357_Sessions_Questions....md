---
title: "Sessions Questions..."
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by bobandirus on 2007-08-25
I was trying to install the beryl theme for ubuntu by following the instructions from this site [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
And got all the way through.. untill i got to the sessions bit.. it says just to make a new session with a new name, but nothing about commands. 

What command should i use??

Im very new to this so keep it simple!

Thank you for any help!

---

### Post by overdrank on 2007-08-25
> **bobandirus said:**
> I was trying to install the beryl theme for ubuntu by following the instructions from this site [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
And got all the way through.. untill i got to the sessions bit.. it says just to make a new session with a new name, but nothing about commands. 

What command should i use??

Im very new to this so keep it simple!

Thank you for any help!

HI it states in the "how to" 
```
beryl-manager
```

---

### Post by bobandirus on 2007-08-25
I tryed using that as the name of the session and the command and nothing happend...

---

### Post by overdrank on 2007-08-25
> **bobandirus said:**
> I tryed using that as the name of the session and the command and nothing happend...

Hi are you using feisty? If you are try using compiz-fusion you can search for it in synaptic manager located under system, administration, synaptic. Beryl and compiz have merged. Good luck!

---

### Post by sailor2001 on 2007-08-25
I think what it's referring to about renaming sessions is this:  Places/home folder  ctrl/h  'gnome2'  'sessions'  change to 'sessions.old' and then ctrl/alt/backspace

---

### Post by bobandirus on 2007-08-25
I have no idea what form of Ubuntu im using, but I have seen a lot of the word Gnome? Also there is no compiz-fusion in the location you said, and there is also nothing there called just synaptic, but there is synaptic packet manager. I tryed compiz-fusion as well and that didnt work. 

Sorry if I sound stupid, im just VERY confuzed because im very new to this....

---

### Post by overdrank on 2007-08-25
> **bobandirus said:**
> I have no idea what form of Ubuntu im using, but I have seen a lot of the word Gnome? Also there is no compiz-fusion in the location you said, and there is also nothing there called just synaptic, but there is synaptic packet manager. I tryed compiz-fusion as well and that didnt work. 

Sorry if I sound stupid, im just VERY confuzed because im very new to this....

OK under system you can select about ubuntu and this will tell you which version you are using. Have you set up your video card for using the desktop effects such as compiz-fusion? And if you can post the output of the command 
```
lspci
```
In the terminal located under applications, accessories, terminal  and tell us which version we might can help you!

---

### Post by bobandirus on 2007-08-25
Im using Ubuntu 7.04 - the Feisty Fawn, installed to make a dual boot sistem with windows XP using WUBI, which i cant remmeber the location off.

The resault of that code is > 
andrew@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 03)
06:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (rev 01)
andrew@ubuntu:~$ 


---

### Post by alienexplorers on 2007-08-25
Are you running the 915 driver for your video card.

---

### Post by overdrank on 2007-08-25
> **bobandirus said:**
> Im using Ubuntu 7.04 - the Feisty Fawn, installed to make a dual boot sistem with windows XP using WUBI, which i cant remmeber the location off.

The resault of that code is

OK this is you graphics card
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
I am sorry but I have not used wubi so I can not help with that. :confused:
There maybe no problem but that I cant say because I dont fully understand how it installs and is used.

---

### Post by bobandirus on 2007-08-25
> **alienexplorers said:**
> Are you running the 915 driver for your video card.

I have no idea, how do i find out?

---

