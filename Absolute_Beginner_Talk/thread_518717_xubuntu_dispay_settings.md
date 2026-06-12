---
title: "xubuntu dispay settings"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-08-06
i want to install Xubutu on laptop in my display settings ive only got 3 to pick from 800x600@56 is where imset at now the rest are lower.

when i star my install to HD i cant see tab to pick setup options.

is there anything i can do to fix this

---

### Post by overdrank on 2007-08-06
> **trucker33377 said:**
> i want to install Xubutu on laptop in my display settings ive only got 3 to pick from 800x600@56 is where imset at now the rest are lower.

when i star my install to HD i cant see tab to pick setup options.

is there anything i can do to fix this

Hi if you want to continue with the install you can just click on the window (single click and hold) with the alt button and move the window. What video card are you using to search if you will have any problems installing the drivers for it?

---

### Post by trucker33377 on 2007-08-06
thxs im not sure what video card this has in it. its a panasonic cf45 NJ

---

### Post by overdrank on 2007-08-06
> **trucker33377 said:**
> thxs im not sure what video card this has in it. its a panasonic cf45 NJ

Ok, a quick search show that model is low power system like 300mhz cpu and 64mb of ram. If you can use the command
```
lspci
```
In the terminal located under applications, accessories, terminal and post the out put here we can find you graphics card and maybe help.

---

### Post by trucker33377 on 2007-08-08
> **overdrank said:**
> Ok, a quick search show that model is low power system like 300mhz cpu and 64mb of ram. If you can use the command
```
lspci
```
In the terminal located under applications, accessories, terminal and post the out put here we can find you graphics card and maybe help.

ok this is a 233 cpu with 160mb ram.

0000:00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
0000:00:01.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:01.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
jumper@jumper-laptop:~$

just a bit slow

---

### Post by overdrank on 2007-08-08
> **trucker33377 said:**
> ok this is a 233 cpu with 160mb ram.

0000:00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
0000:00:01.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:01.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
[COLOR="Red"]0000:00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] [/COLOR](rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
jumper@jumper-laptop:~$

just a bit slow

Ok you graphics card is highlighted and I found this thread that may help
[http://ubuntuforums.org/showthread.php?t=197365&highlight=Neomagic+Corporation+NM2160](http://ubuntuforums.org/showthread.php?t=197365&highlight=Neomagic+Corporation+NM2160)

Good luck! :popcorn:

---

### Post by trucker33377 on 2007-08-08
well i went thru reconfigure with xorg. it looks like 800 by 600 is best i can do here. all in all its not to bad for this old laptop. its still a bit slow but hay what can you do with a $40 computer,  lol

xubuntu has a media player XMMS, it is not playing right . i get half way thru the song before any sound comes thru. i would think this is due to low ram or cpu. is there any way to set it up so it loads the file then starts? or maybe a diff media player. i do have this same laptop with windows 98 se loaded in it and it will play on that OS. just thinking here what did linux use back in 1999?

---

