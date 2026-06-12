---
title: "Like many others on here I need help with an Acer!"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by ox720 on 2007-09-12
Hello all 
After spending around three days searching the various threads on this forum regarding getting wireless to work on an Acer, I have given up searching and decided to ask you wise and wonderful people out there directly for help! 

Some background for you:

I have an Acer Travelmate 4401 LCI, it has a AMD 64 processor and I believe an Broadcom 802.11 b/g wireless LAN card. 

I was previously running Windows XP professional and I have fully installed Ubuntu 7.04 or I believe it's referred to as Feisty Fawn.

As I said I have searched and tried the options on some of the threads on here without sucess, this leaves me with the following conclusions:
I am doing something wrong (probable) 
My laptop is not driver is not compatible (possible?)
combination of the above (most likely)

Any help would be graciously received and who knows, if your ever in Sheffield I'll buy you a beer

---

### Post by ox720 on 2007-09-12
I posted this on a different part of the forum but I think I may get a better response on here so here's the link. It concerns Acer and wireless 

[http://ubuntuforums.org/showthread.php?t=549386]("http://ubuntuforums.org/showthread.php?t=549386")

---

### Post by overdrank on 2007-09-12
> **ox720 said:**
> I posted this on a different part of the forum but I think I may get a better response on here so here's the link. It concerns Acer and wireless 

[http://ubuntuforums.org/showthread.php?t=549386]("http://ubuntuforums.org/showthread.php?t=549386")

Hi can you post the out put of the command in the terminal 
```
lspci
```
The terminal is located under applications, accessories, terminal it will help us get details on your wireless card.

---

### Post by ox720 on 2007-09-12
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

---

### Post by overdrank on 2007-09-12
> **ox720 said:**
> 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
[COLOR="Red"]06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

Hi and welcome, I have highlighted wireless card and this link looks like it has good info Good luck! 
[http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom+Corporation+BCM4318](http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom+Corporation+BCM4318)
Or you may choose this one
[http://ubuntuforums.org/showthread.php?t=190177&highlight=Broadcom+Corporation+BCM4318](http://ubuntuforums.org/showthread.php?t=190177&highlight=Broadcom+Corporation+BCM4318)

---

### Post by angliski on 2007-09-12
HAVE YOU TRIED THE sTICKY hOW TO ENABLE bROADCOMXX CARDS AT THE HEAD OF THIS FORUM THREAD.
i HAD PROBLEMS WITH IT UNTIL i CHECKED THE DOWNLOADED TAR FILE AND AFTER EXTRACTING IT FOUND THAT SOME OF TEH FILES WERE MISSING. I WAS ABLE TO DOWNLOAD IT AGAIN ON ANOTHER COMPUTER, (THE OFFLINE INNSTALLATION FILE) WHICH I BURNED TO A CD AND THEN COPIED IT TO MY DESKTOP. IT THEN INSTALLED WITH NO PROBLEM AS PER THE STICKY.
HOPE THIS HELPS
STEVE.

pS MY LAPTOP IS AN ACER ASPIRE 5012

---

### Post by ox720 on 2007-09-28
Right current update....I have tried the above suggestions and many others and still have had no luck with getting the wireless to work. This lead me to spit my dummy out, take the ball home and not play anymore, surviving on wired internet access for a few weeks. I am now ready to try again so any further suggestions on how to get this thing wireless are still most welcome. One thing I have noticed, I seam to have lost the ability to boot up Windows xp?

---

### Post by NullHead on 2007-09-28
> **ox720 said:**
> Right current update....I have tried the above suggestions and many others and still have had no luck with getting the wireless to work. This lead me to spit my dummy out, take the ball home and not play anymore, surviving on wired internet access for a few weeks. I am now ready to try again so any further suggestions on how to get this thing wireless are still most welcome. One thing I have noticed, I seam to have lost the ability to boot up Windows xp?

well I have the same card and I have it working quit nicely. So ill try my best to help you with yours. 

so start up a terminal and then we need to stop the bad driver from loading
```
sudo gedit /etc/modprobe.d/blacklist 
```
Then add the line ```
blacklist bcm43xx
``` 
down at the bottom of the list

then ```
sudo rmmod bcm43xx
```

ok now I'm writing this for 7.04 ... and both 32 and 64 bits 

so now to install ndiswrapper.

ok now download [the first package]("http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb") and then double click on it and install it. Then download the [64bit one]("http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_amd64.deb") or the [32bit  one]("http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb") double click on witch ever package you downloaded and install it.

Then go down to the end of my post and download one of the drivers I've uploaded either 32bit or 64bit. 

then after you've done that unpack them with fileroller or what ever you like. There will be a folder inside each of the files. If you unzip them make shure they go to you home directory. Then time to install them into ndiswrapper.```
sudo ndiswrapper -i bcmwl5.inf
```
then to make them start up. ```
sudo ndiswrapper -m
```
and then restart you computer and it *should* work ... well it does for me.

---

### Post by ox720 on 2007-09-28
I have pasted this into the Terminal sudo gedit /e blacklist bcm43xx
sudo and it brought up a window *e(/) - gedit

---

### Post by ox720 on 2007-09-28
> **NullHead said:**
> well I have the same card and I have it working quit nicely. So ill try my best to help you with yours. 

we need to stop the bad driver from loading
```
sudo gedit /e blacklist bcm43xx
sudo 
```

Sorry just figured it out, I have blacklisted the bcm43xx Whats next?

---

### Post by NullHead on 2007-09-28
No I'm sorry I had problems with my browser and it saved my post... I've added allot more info.

---

### Post by ox720 on 2007-09-28
After installing the drivers it said they were already installed? After restarting I checked the network settings and a wireless connection is showing but the light I can't connect to the net without a wire? There used to be a light that indicated the wireless was active and this is not lit up?

---

### Post by NullHead on 2007-09-28
Do you have a button on you keyboard to turn this on? On a Dell 1505 it like f4 or something like that. Please give me the output of ```
ndiswrapper -l
```

---

### Post by ox720 on 2007-09-28
ox@ox-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
ox@ox-laptop:~$

---

### Post by ox720 on 2007-09-28
not sure about a button to turn it on? It always came on when I switched the laptop on, none of the function f keys look like they have anything to do with wireless?

---

### Post by NullHead on 2007-09-28
> **ox720 said:**
> After installing the drivers it said they were already installed? After restarting I checked the network settings and a wireless connection is showing but the light I can't connect to the net without a wire? There used to be a light that indicated the wireless was active and this is not lit up?

> **ox720 said:**
> ox@ox-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
ox@ox-laptop:~$

ok well you can see the wireless network can't you? What version of Ubuntu are you using? Do you have network-manager-gnome installed? As for the light I don't know you might check your manual for a button that you might be able to press.

---

### Post by ox720 on 2007-09-28
Yeh I have the manager installed.....Thanks for trying anyway!

---

### Post by NullHead on 2007-09-28
Can see your wireless network using that applet?

---

