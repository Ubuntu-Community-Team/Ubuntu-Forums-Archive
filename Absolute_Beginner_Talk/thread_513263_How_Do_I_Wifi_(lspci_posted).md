---
title: "How Do I Wifi? (lspci posted)"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by JAYCEE1 on 2007-07-30
Just got a new-to-me Dell Latitude C400 with Ubuntu. 

I have never used a Wifi connection. How do I connect to the internet through the Wifi card.

Here is lspci:

```

dell:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801  Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM  AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM  AC'97 Modem Controller (rev 02)
02:00.0 Ethernet controller: 3Com Corporation 3c905c-Tx/Tx-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Insturments PCI1410 PC cardbus Controller (rev 03)
dell:~$

```

I had to type in the output since the new computer is not connected to the internet.

Thanks!

---

### Post by walkerk on 2007-07-30
i'm not seeing a wireless card.. you do have one, corret? 1390, 1490, 4xxx?

---

### Post by walkerk on 2007-07-30
> **JAYCEE1 said:**
> Just got a new-to-me Dell Latitude C400 with Ubuntu. 

I have never used a Wifi connection. How do I connect to the internet through the Wifi card.

Here is lspci:

```

dell:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801  Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM  AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM  AC'97 Modem Controller (rev 02)
02:00.0 Ethernet controller: 3Com Corporation 3c905c-Tx/Tx-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Insturments PCI1410 PC cardbus Controller (rev 03)
dell:~$

```

I had to type in the output since the new computer is not connected to the internet.

Thanks!

```
lspci | grep Network
```

---

### Post by diatribe on 2007-07-30
yes you should have something like: 

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


I dont think you have a wireless card man

Edit: from a review on your particular computer - Wireless 802.11b connectivity costs extra

---

### Post by JAYCEE1 on 2007-07-30
Thanks walkerk!

lspci | grep Network returns this:

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Thanks all!

---

### Post by diatribe on 2007-07-30
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)
or you could try using wicd, [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by ugm6hr on 2007-07-30
This is pretty successful for BCM cards:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

And I don't think Wicd will solve this issue by itself :(  Although it is a great solution for most!

---

### Post by JAYCEE1 on 2007-07-30
Here is the history output. Is the Broadcom setup or do I still need ndiswrapper?
```

1 lspci | grep Broadcom\ Corporation
2 0000:02:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
3 echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
4 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -0- | sudo apt-key add - && sudo apt-get update
5 sudo lshw
6 sudo lshw

```

Thanks!

---

### Post by diatribe on 2007-07-30
well from the looks of it you just added the repository, so unless it is magically working now I would think it still needs to be setup

---

### Post by ugm6hr on 2007-07-30
> **JAYCEE1 said:**
> Here is the history output. Is the Broadcom setup or do I still need ndiswrapper?


```
lshw -C network
```
This will tell you what driver you are using.

Which how-to did you use?

---

### Post by JAYCEE1 on 2007-07-30
Ok. Thanks!

---

### Post by JAYCEE1 on 2007-07-30
I didn't type those commands in. The previous owner did.

I typed in lshw -C network and it returned quite a lot of info. The driver for *-network:1 (the wireless interface) is driver=bcm43xx driverversion=2.6.20-16-gener

---

### Post by diatribe on 2007-07-30
Just follow the directions from either one of the how-tos which have been posted

---

