---
title: "[SOLVED] Total linux noob. Looking for some help!"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by ashehudson on 2008-03-10
First, I love how helpful everyone in the linux community is!

I've been using Ubuntu for 10 days now! About day 3, I got my wireless card working. Not really sure how, I kinda just did a lot of research and downloaded a bunch of random wireless drivers until it worked.

Once it started working, I got so excited about Ubuntu that I decided to make it my OS of choice from now on, so just like any other wide eye kid, I saw the 8.04 alpha download and upgraded my Ubuntu. The only thing that stopped working was the wireless card.

So rather then do my shotgun solution, I want to find out how to fix it. I found the two drivers I need to download and I'm in the middle of trying to fix it again, but I was hoping to get an answer about what broke it in the first place. (The drivers seem to still be installed)

Thanks!

Kevin

---

### Post by Presto123 on 2008-03-10
8.04 is still in development, so, basically...not a good move for someone new. You will most likely have various issues until a little bit after the final release.

Post the output of this in code tags (typed in Terminal):
```
lspci
```

---

### Post by jcwmoore on 2008-03-10
I think you got a little too excited, Hardy will be out in a month or so.... I was like this the last time around and upgraded to 7.10 about a month before it was officially released, a lot of things were broke and I went back.  I would not recommend using the new release until it is a release candidate, but if you just can't wait, like me..., use virtual box and install 8.04 as a VM to test it out and play around...

---

### Post by Presto123 on 2008-03-10
> **jcwmoore said:**
> I think you got a little too excited, Hardy will be out in a month or so.... I was like this the last time around and upgraded to 7.10 about a month before it was officially released, a lot of things were broke and I went back.  I would not recommend using the new release until it is a release candidate, but if you just can't wait, like me..., use virtual box and install 8.04 as a VM to test it out and play around...
+1

---

### Post by ashehudson on 2008-03-10
Understood. For some reason I had it in my head that the update would only add to my features. Like I said though, only having it on this computer for 10 days, I really didn't have much to lose. I just realized that my sound isn't working either. I hope the bug reports that I've been attempting to send will at least help the devs.

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by ashehudson on 2008-03-10
Is that what you were wanting me to post?

---

### Post by Presto123 on 2008-03-10
Yeah, thanks.

Try following this how-to and tell me if it works:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29#preview)

---

### Post by EnergySamus on 2008-03-10
Dude, It is a broadcom controller, download the files from this link on to your computer (through your cable, DSL... Assuming that you have one!!!

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

It says Ubuntu 7.10, but I think that it will work!

EnergySamus

---

### Post by ashehudson on 2008-03-10
Yeah, I've installed both of those and it still no dice. Guess I'll have to use this prehistoric wired connection for another month.

---

### Post by ashehudson on 2008-03-10
Hrm, I reinstalled the drivers and this time it upgraded the firmware, seems to be working great now and the sound is working too.

---

### Post by DUDE_2000 on 2008-03-10
whoops, answered after I started..


have you tried ndiswrapper?
My card doesn't work with the firmware, but, if you install ndiswrapper, and ndiswrapper utils (you need both), and set up the driver(not hard) reboot, and it should work.

To set up the driver:

1. Get the driver correct for you system (you need a different one if you have a 64 bit system), you need both the .inf, and the .sys

2. put the driver in a directory structure you know, say on you desktop (/home/<login name here>/Desktop/driver.inf)

3. open up the terminal, and type
$ ndiswrapper -1
to see what all the options are

4. then type 
$ ndiswrapper -i (in here goes the directory structure where you put the driver)

5. then
$ ndiswrapper -m
and, after

$ ndiswrapper -mi

then
$ ndiswrapper -l
to see if it was installed properly


hope this helps!

---

### Post by EnergySamus on 2008-03-11
Nice!!! That link worked for me, and I had a feeling that it would work for you! 
I found that link from the forums...

Anyway, glad that I could help:)

EnergySamus

---

