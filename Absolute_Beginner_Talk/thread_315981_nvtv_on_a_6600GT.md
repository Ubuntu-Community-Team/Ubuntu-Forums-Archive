---
title: "nvtv on a 6600GT"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by twtmc on 2006-12-10
I am fairly new to ubuntu, and I am trying to get tv out working without having to take the risk of messing up my system (I tried a how to guide on how to edit the xorg.conf file, which lead to a blue error screen on reboot). I installed it easily enough, but when I try to launch it I get an error message reading "Fatal: No supported video card found." From what I have read, nvtv should work on all newer nvidia cards. How can I fix this?

---

### Post by dboyd13 on 2007-04-30
I'm experiencing the same problem on 6600 standard.

---

### Post by Drakkor on 2007-04-30
Have you tried tvtime?  :)

---

### Post by Drakkor on 2007-04-30
Can you post
```
lspci
```

---

### Post by dboyd13 on 2007-05-01
At work at the moment. Will submit my lspci as soon as I get home. Thanks for the assistance.

---

### Post by dboyd13 on 2007-05-01
Ok, I was surprisingly able to get my fiancé to run the command for me at home :). Here is the output:

```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller 
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller 
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 04)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI 
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
02: 03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
```

---

### Post by puterboy on 2007-06-09
I seem to have a solution. I'm using a 6600gt on ubuntu 6.06 amd64

First off, i didn't use nvtv. i used envy, which configured all my settings for me. maybe it's cheating, but whatever.....after it installed the packages and stuff i needed, nvtv STILL wouldn't work, despite finally seeing the NVIDIA splash screen. so I went into 

Applications>System Tools>NVIDIA X Server Settings

I went to the X Server Display Configuration, clicked on my TV (which it had never detected before), and configured it (I put my screen to the right of screen 0, my PC monitor. I couldn't apply settings, so I saved it and restarted. It didn't work after restarting my X Server (Ctrl+Alt+Shift+Backspace). I found that the file didn't have the correct permissions, so i used

sudo chmod a+rwx /etc/X11/xorg.conf

to let me write it. I couldn't seem to keep any settings by overwriting the file, so I had to save the xorg.conf from the settings panel on my desktop, open both, and paste over the contents of the old file with the new one. worked like a charm. i'm so newbish, but it works now. any questions, feel free to PM me, i'll try to help as much as I can.

Also, after every reboot of the X server, you need to reconfigure your TV setting in the panel, because if it didn't work, it'll overwrite the settings to where your TV is disabled.

Hope it works!!!

---

### Post by dboyd13 on 2007-06-12
With persistence comes success!

Thanks PuterBoy for your suggestions and I finally got it right. But my worry is that I have it right several times before!, because I found that the cable I was using was faulty. Previously The nvidia-settings app was able to detect the TV, but not actually display anything. Your post confirmed that I was doing the right configuration, so that is what led me to find that the cable was damaged :)

I often find that due to the complexity of linux configuration (esp. xorg.conf) I keep working on the configuration, rather than looking into the fundamentals (like cables!).

---

