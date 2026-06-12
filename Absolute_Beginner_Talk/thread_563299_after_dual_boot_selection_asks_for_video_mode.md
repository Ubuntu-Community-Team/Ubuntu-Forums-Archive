---
title: "after dual boot selection asks for video mode"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by slymi2005 on 2007-09-29
After I make my selection at the dual boot menu I am asked about a screen mode it says press enter or 'scan' and then it shows a list of different modes it also says something about vga. Any idea what this is? Sorry if this is sort of unclear.

---

### Post by overdrank on 2007-09-29
> **slymi2005 said:**
> After I make my selection at the dual boot menu I am asked about a screen mode it says press enter or 'scan' and then it shows a list of different modes it also says something about vga. Any idea what this is? Sorry if this is sort of unclear.

Hi could you tell us the specs on your system? And do you have two video cards installed? Maybe onboard and then and agp or pci slot?

---

### Post by slymi2005 on 2007-09-29
intel celeron 800 mhz, 380 mb ram, hp pavilian, intel built in graphics, I don't know what else you need.

---

### Post by overdrank on 2007-09-29
> **slymi2005 said:**
> intel celeron 800 mhz, 380 mb ram, hp pavilian, intel built in graphics, I don't know what else you need.

Hi and yes if you don't mind could you post the output of the command in the terminal 
```
lspci
```

---

### Post by slymi2005 on 2007-09-29
00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
01:0b.0 Communication controller: Agere Systems LT WinModem
01:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
01:0e.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)

---

### Post by overdrank on 2007-09-29
Ok this is the first that I have encounter this error or option and the output of the lspci command looks ok so I have no answer for you. :(

---

### Post by slymi2005 on 2007-09-30
My problem occurs when i turn my computer on and then the boot menu appears and i select ubuntu and then it says failed to initiate screen/video mode, enter mode or press return, then i hit enter and it shows a list of things and then it says enter mode, or 'scan' and i just hit enter and then it continues loading. this recently started happening, before i just selected ubuntu and it would load to the log in screen. if anyone knows how to fix this that would be great.

---

### Post by slymi2005 on 2007-10-26
bump

---

### Post by overdrank on 2007-10-27
> **slymi2005 said:**
> bump

Hi and have you tried booting in recovery mode. It should be the second choice on the list when booting. If you can the try and reconfigure your xorg with this command ```
sudo dpkg-reconfigure xserver-xorg
``` answer a few questions and if you don't know the answer the leave as the default answer given. Hope this helps. :KS

---

### Post by slymi2005 on 2007-11-11
i did this and it didn't fix my problem. Also, when I log in the splash screen shows up and it loads up but the screen stays orange and I can't see anything. I am able to log in on other accounts but when i try opening the terminal the computer restarts by itself and i'm sent to the login screen. what's going on?

---

