---
title: "onboard graphics"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-11-10
here is the output of lspci:

```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03
)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media I
O] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev
 a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound                                                                                                                        Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller                                                                                                                        (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller                                                                                                                        (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa                                                                                                                       st Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controlle                                                                                                                       r (rev 02)
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]                                                                                                                        802.11g Wireless LAN Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp                                                                                                                       erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add                                                                                                                       ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA                                                                                                                       M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

```

I need to install my audio and display drivers can anyone point me in the right direction please?
I am extremely weary of messing with xorg.conf now since I totally messed my system up resulting in a reformat recently. :( 

Thanks very much, Tom

---

### Post by renzokuken on 2006-11-10
if you back up your xorg.conf before you make any changes, if it all goes pete tong then all u have to do is copy back the working xorg.conf and you are as you were

so before you make any changes, from the xorg.conf parent folder

```
sudo cp xorg.conf xorg.conf_backup
```

make your changes, and if it all goes wrong and you need to change back, boot into text/terminal mode

```
sudo cp xorg.conf_backup xorg.conf
```

if you do this you should never have to reformat if you screw up your xorg.conf

as for your display drivers, u have onboard grafix so you should not need drivers really, VGA mode should just work

---

### Post by tommy1987 on 2006-11-10
Is there anyway I can get higher resolutions than I am currently getting (1024x768)? Everything is far too big!

---

### Post by renzokuken on 2006-11-13
just edit your xorg.conf and add in the new resolutions u want, although it may be easier to do the following

```
sudo dpkg-reconfigure xserver-xorg
```

and just select the resolutions u want. and just accept any other choices it give you (**back up your xorg.conf first**)

have a look at this thread
[http://www.ubuntuforums.org/showthread.php?t=297894&highlight=xorg.conf](http://www.ubuntuforums.org/showthread.php?t=297894&highlight=xorg.conf)

---

### Post by jd65pl on 2006-11-13
I have pretty much the same out put of lspci, the vesa driver works for the display with no hardware rendering, the sis graphics driver works but not when I have an external monitor.

I have an acer laptop 3003lc.

---

### Post by dannyboy79 on 2006-11-13
you shoulddn't have to install any drivers for linux, i have the same onboard graphics and it worked by default. you also don't need to play with your xorg.conf, have you gone to settings, admin, display settings? there should be a choice for 1280x1024? mine worked but I couldn't get any graphics acceleration or opengl etc etc so I just went out and bought a geforce 6200 and all is good now and I get awesome performance. i have the same ethernet controller, sound controller as well. does the sound come out of BOTH your speakers? it did at first for me but now it only comes out the left speaker? and no one has been able to help me with this. :-( anyway, all your hardware should be working out of the box as mine did. i just didn't like the graphics, couldn't even play dvd's without horrible performance just so you know.

---

