---
title: "screen resolution problems - ubuntu 7.10"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by alloftheabove on 2008-02-07
hello.  It seems I am having a common ubuntu problem.  I want my screen res to be (preferably) 1024 by 768, so I went into screens and graphics and changed a couple things ( chose widescreen screen option and changed the screen res to 1024 by 768).  Unfortunately, when I rebooted, it told me it was in low graphics mode, then sent me to the normal-looking login screen.  On top of not remembering my prefs, it reset it to 800 by 600 ( way too large for me), and now I can't even choose 1024 by 768.  I know people are going to ask for ```
lspci
```, so here it is:
```

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
02:0b.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

```

I've heard about x-server but I don't understand it.  Any help would be appreciated.

---

### Post by alloftheabove on 2008-02-07
bump *sigh*

---

### Post by Crumpets and Jam on 2008-02-07
Are there any Restricted Drivers for your card?

Go to:

System --> Administration --> Restricted Drivers.

Install them if there are any.

---

### Post by 77midget on 2008-02-07
well, I am a noob, but i had the same problem this week on my first install, and was able to get past it. I have a Dell Precision M70 w/ an NVidia Quadra 1400 card. The install put in a 'custom' entry and I was able to run at the optimal, which is 1680x1050.However, when I tried to get my SGI SW1600 to go multiple display for me in my dock, the same thing happened that you have. The way I resolved it was to set the display to generic @ 680x480 (or whatever that aspect ratio is), and going into the synaptic PM and uninstalling the NVidia packages. Then I ran a PM update, and re-installed the packages. Once that was done, I reconfigured the card w/ the NVidia Riva 128/Riva TNT etc driver, then set it to Generic LCD widscreen 1680x1050. It is working fine. Since I have only been in linux for a couple days, I am sure that it is not optimal, but it is fine for now.

Still cannot get LT screen and SGI panel to work together when docked tho.

---

### Post by alloftheabove on 2008-02-07
Thanks, seems like it worked (at least for now)!

---

