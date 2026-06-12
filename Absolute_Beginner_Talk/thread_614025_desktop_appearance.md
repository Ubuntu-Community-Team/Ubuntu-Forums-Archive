---
title: "desktop appearance"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2007-11-15
when i try to check the box containing custom desktop effects, its tells me that desktop effects could not be enabled...
what do i do so then i can enable custom desktop effects?

---

### Post by overdrank on 2007-11-15
> **dylondadank said:**
> when i try to check the box containing custom desktop effects, its tells me that desktop effects could not be enabled...
what do i do so then i can enable custom desktop effects?

Hi and you will need to install the drivers for the graphics card. What is the model of the graphics card and maybe we can help.

---

### Post by dylondadank on 2007-11-15
> **overdrank said:**
> Hi and you will need to install the drivers for the graphics card. What is the model of the graphics card and maybe we can help.

honestly i have no idea

---

### Post by overdrank on 2007-11-15
> **dylondadank said:**
> honestly i have no idea

You an post the output of this command in the terminal ```
lspci
``` the terminal is located under applications, accessories

---

### Post by dylondadank on 2007-11-15
> **overdrank said:**
> You an post the output of this command in the terminal ```
lspci
``` the terminal is located under applications, accessories

dylan@chaos:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

### Post by LowSky on 2007-11-15
go to the menu

System>Admin>Restricted Drivers
in that menu Enable restricted drivers

---

### Post by mysticrider92 on 2007-11-15
The 'Restricted Drivers Manager' can help install your graphics card driver for you, I think it is in the System>Administration menu (I am not on Ubuntu right now). 

Once it has installed the correct driver, you will need to press Control>Alt>Backspace and login again. You should now be able to start desktop-effects.

Also, if you want to find your graphics card model, open a terminal and type "lspci".

[edit] overdrank beat me to it, you have an ATi Radeon Xpress 200 card (last line of lspci output).

---

### Post by dylondadank on 2007-11-15
> **mysticrider92 said:**
> The 'Restricted Drivers Manager' can help install your graphics card driver for you, I think it is in the System>Administration menu (I am not on Ubuntu right now). 

Once it has installed the correct driver, you will need to press Control>Alt>Backspace and login again. You should now be able to start desktop-effects.

Also, if you want to find your graphics card model, open a terminal and type "lspci".

[edit] overdrank beat me to it, you have an ATi Radeon Xpress 200 card (last line of lspci output).

alright, now when i try it says "The Composite extension is not available"

---

### Post by ~&#730;JaZ&#730;~ on 2007-11-15
hi!
I have the same problem...after i installed the drivers form my graphic card...when i try to enable the desktop efects...i get "The Composite extension is not available"... when i tried beryl or compiz it just dosent wanna start the effects...any help...pls?!...
tnx
z.

---

### Post by Tyke91 on 2007-11-15
the program 'Envy' can help you to install graphics drivers for ATI and Nvidia

it's in the repositories

---

### Post by boriquajake on 2007-11-15
> **Tyke91 said:**
> the program 'Envy' can help you to install graphics drivers for ATI and Nvidia

it's in the repositories

I am having the same problem as the other fellow. I did a search in the package manager for anything called "Envy" and selected for install whatever it was that came up. What should I do next, if you don't mind me butting in to the conversation. :)

---

