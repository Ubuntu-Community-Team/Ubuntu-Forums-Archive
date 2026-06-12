---
title: "Poor video performance"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-12-31
Hello again,
I've got a linux box here with an MSI board in it. The board has built in sound, video, and network. All seem to be working, but the performance of the video is horrid (I can watch it paint the screen). Can someone walk me through the steps of getting this thing to work better?

Thanks,
WIll

---

### Post by benjjo on 2006-12-31
Have you had a look at [this page]("http://www.ubuntuforums.org/showthread.php?t=186792") yet? If so just disregard my annoyance.

---

### Post by gantww on 2006-12-31
I guess I probably should have clarified my problem a bit. When I meant video, I didn't mean video as in playing video. I meant video as in just GUI interfaces in general. The thing barely crawls along.

That said, thanks for the link. That will probably help out a ton on the machine that I'm setting up tomorrow.

---

### Post by taurus on 2006-12-31
Paste the output of this command from a terminal?

```
lspci
```

---

### Post by gantww on 2006-12-31
00:00.0 Host bridge: VIA Technologies, Inc. Unknown device 0336
00:00.1 Host bridge: VIA Technologies, Inc. Unknown device 1336
00:00.2 Host bridge: VIA Technologies, Inc. Unknown device 2336
00:00.3 Host bridge: VIA Technologies, Inc. Unknown device 3336
00:00.4 Host bridge: VIA Technologies, Inc. Unknown device 4336
00:00.5 PIC: VIA Technologies, Inc. Unknown device 5336
00:00.7 Host bridge: VIA Technologies, Inc. Unknown device 7336
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCIE Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 11)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

---

### Post by gantww on 2007-01-01
It looks like it doesn't have any idea about the VGA controller. I still have all the materials for the motherboard. How can I figure out what it is so that I can make it work?

---

### Post by MkfIbK7a on 2007-01-01
you probably need a driver for your video card

---

### Post by d3v1ant_0n3 on 2007-01-01
Ok, you're running a via chipset mobo with an AMD processor, so I'll assume you don't have an Intel graphics chipet:

[ How to install Nvidia drivers on Edgy](http://ubuntuforums.org/showthread.php?t=281823&highlight=install+nvidia)
[how to install Ati drivers](http://ubuntuforums.org/showthread.php?t=75378&highlight=ati)

---

### Post by Atomic Dog on 2007-01-02
You could always buy a cheap video card.  You could find something OK for probably $40.

---

### Post by gantww on 2007-01-02
It looks like the video chip is a VIA K8M890. They don't appear to offer any linux drivers. Is there a place to get linux drivers for VIA chipsets?

---

### Post by Tintazul on 2007-01-09
> **gantww said:**
> It looks like the video chip is a VIA K8M890. They don't appear to offer any linux drivers. Is there a place to get linux drivers for VIA chipsets?

I had the same motherboard and the same problem. I found out that the Integrated Graphics Processor is a VIA Chrome9, then installed OpenChrome using the following - 

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Kudos to those who wrote that tutorial! It worked seamlessly.

---

### Post by Ben Sprinkle on 2007-01-09
Easy easy.
```

sudo dpkg-reconfigure xserver-xorg

```
When you get to the screen about the video drivers, change it from the default VESA and find your driver, if you don't have it go install. :)
After that reboot, all your windows, apps and what have you will be speedy and real time scrolling. Not that laggy crap, I used to have this issue. ;)

---

