---
title: "pcmcia port not powering (wireless) card"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by ssho on 2007-11-08
Newbe user.  

Old Dell latitude CPi laptop circa around 1986.  PentiumII 400mhz 256ram.   Installed xubuntu Gutsy Gibbon as a dual boot.  Have been running XP successfully.   

The only access this computer has to get to the internet is through it's PCMCIA wireless card.  The PCMCIA port/wireless card works fine in XP.  The computer does not have a built in ethernet card.  

When running Gutsy Gibbon I can't seem to get the wireless card to powerup let alone work.  There is nothing in the bios about the port and since it works in XP I don't know what the next step I should take is.  

XP says the PCMCIA adapters are Texas Instruments PCI-1225 CardBus Controller.  
The wireless card is a Dlink DWL-G650M.  

Suggestions?

:confused:

---

### Post by overdrank on 2007-11-08
> **ssho said:**
> Newbe user.  

Old Dell latitude CPi laptop circa around 1986.  PentiumII 400mhz 256ram.   Installed xubuntu Gutsy Gibbon as a dual boot.  Have been running XP successfully.   

The only access this computer has to get to the internet is through it's PCMCIA wireless card.  The PCMCIA port/wireless card works fine in XP.  The computer does not have a built in ethernet card.  

When running Gutsy Gibbon I can't seem to get the wireless card to powerup let alone work.  There is nothing in the bios about the port and since it works in XP I don't know what the next step I should take is.  

XP says the PCMCIA adapters are Texas Instruments PCI-1225 CardBus Controller.  
The wireless card is a Dlink DWL-G650M.  

Suggestions?

:confused:

Hi and welcome, it appears that card uses a Atheros chipset. I would recommend to use the command in the terminal ```
lspci
``` and confirm. Then terminal is located under applications, accessories, terminal. Also have you checked under applications, system, network to see if the card is activated?

---

### Post by ssho on 2007-11-09
Sorry for the slow response.  This working for a living gets in my way of good stuff like this.  

> **overdrank said:**
> Hi and welcome, it appears that card uses a Atheros chipset. I would recommend to use the command in the terminal ```
lspci
``` and confirm. Then terminal is located under applications, accessories, terminal. 

I tried to run terminal.  When I start the program the screen goes blank for a few seconds then about 6 lines of some code appear for a few seconds and then I'm asked to re-log on wth my user name and password.  Once I log back on I'm right back to the desktop.  Does that mean the application crashed?  

> **overdrank said:**
>  Also have you checked under applications, system, network to see if the card is activated?

The only item is a modem for dialup.  No network card at all shows up.

---

### Post by ssho on 2007-11-11
> **ssho said:**
> 


I tried to run terminal.  When I start the program the screen goes blank for a few seconds then about 6 lines of some code appear for a few seconds and then I'm asked to re-log on wth my user name and password.  Once I log back on I'm right back to the desktop.  Does that mean the application crashed?  

REVISED 11/11/07: 

I found that the terminal was crashing.  I found this bug report:  

[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849)

It took me much research to perform the simple task of changing the display from 24 to 16 using the sudo editor.  Well, at least I learned something there.  Anyways, once I got the terminal program working, here is the text:

----------------------

frodo@frodo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: Neomagic Corporation NM2360 [MagicMedia 256ZX]
01:00.1 Multimedia audio controller: Neomagic Corporation NM2360 [MagicMedia 256ZX Audio]
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5005VL 802.11bg Wireless NIC (rev 01)
frodo@frodo-laptop:~$ 
frodo@frodo-laptop:~$

---------------------

I'm not sure what all that means and if it's good or bad, but that is what was displayed using the lspci command  

Also, as I noted, the only item under applications, system, network is a modem for dialup.  No network card at all shows up.

Steve

---

### Post by ssho on 2007-11-14
Does anyone have an idea for me? 

EDIT:  Sorry to be a pest but I'm stuck.  I can't access the internet without a wireless card as the laptop does not have an ethernet port so I think once I can get the wireless card to work, I should be OK.  

Anyone know what me next step is?  I'm really a newbie so if someone could point me to a step by step process I would greatly appreciate it.  

Steve_

---

### Post by ssho on 2007-11-26
Bump...

---

### Post by jimrz on 2007-11-26
Do you get a message when you boot that your BIOS date is older than the year 2000 and that in order to get acpi you need to use "acpi=force"? If so, this may help:

I have an old ThinkPad 600x and ubuntu sees the BIOS date as <2000 and therefore will not load the acpi module automatically, so I have to ad the kernel parameter
```
acpi=force
```
to get acpi working. However, when I do this by itself my pcmia cards (D-link nic + Netgear wifi, also atheros but different chipset) no longer work. To fix this I also add
```
pci=noacpi
``` 
as a kernel parameter in /boot/grub/menu.lst. With these additions all works as it should.

---

