---
title: "Finding the PCI ID of the Video Card"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Jenny201 on 2007-03-19
Hello there,

I'm trying to find the correct PCI ID of my graphic card so I can put in the configuration menu: 'sudo dpkg-reconfigure xserver-xorg' for 'Please enter the video card's bus identifier'.



So I entered LSPCI and I do get these pci number. But when I try to insert that in the configuration menu, it tells that the code is not in correct format. It should be in this format PCI:0:00:0. 
Here is what I get when I type LSPCI: 

0000:01:0b.0 VGA Compatible controller: nVidia Corporation NV17 (GeForce4 MX 440)


thanks :)

---

### Post by Jenny201 on 2007-03-19
any ideas guy?

---

### Post by 67GTA on 2007-03-19
Run a terminal and type "lspci"

---

### Post by 67GTA on 2007-03-19
Run a terminal and type "lspci". That will list all of your pci devices .

---

### Post by Jenny201 on 2007-03-19
> **67GTA said:**
> Run a terminal and type "lspci". That will list all of your pci devices .

Ubuntu does not load fully for me so I'm doing all this through the command menu. I'm new to this so can you tell me how can I run a terminal through this?

:) :KS

---

### Post by 67GTA on 2007-03-19
I was refering to opening a terminal while in GUI mode, but if you are using text commands now, you should be able to type that in where you are at.

---

### Post by alienexplorers on 2007-03-19
Your PCI command should be "PCI :1:0b:0" <------ remove quotes

---

### Post by Jenny201 on 2007-03-19
it still says not in correct format.


:(

---

### Post by 67GTA on 2007-03-19
It should autodetect the pci id for you. What type of PCare you installing on?

---

### Post by Angus MacDoodles on 2007-03-25
> **Jenny201 said:**
> it still says not in correct format.


:(

I'm having the exact same problem as Jenny201 -  I cannot get the configure utility to recognize the PCI bus address formatting when adding a ATI R128 video card. (as opposed to the OE on-board Intel)
lspci reports 0000:01.0b.0 for the ATI - have tried 1:0:0, 1:b:0, 1:0b:0 and several other "variations on a theme." All were rejected for improper format. 

The machine will NOT autodetect the ATI add-on card, only the OE Intel onboard (it doesn't seem to look any further and give me any options) - thus, the need to "force" the correct PCI address. 

BIOS settings are not a problem: this is a jumperless mother-board and the BIOS auto-detects the additional card (have verified in BiOS settings that it is recognizing the PCI board as the one to use.)

any help on using the proper address format would be appreciated....... TIA

Machine: old HP Paviliion Celeron 636mhz
Memory: 384 MB
OS: Ubuntu 6.06 Dapper (alt install, only OS on machine)

---

### Post by guapo on 2007-04-07
Jenny201 and Angus MacDoodles

Unfortunately dpkg-reconfigure does not understand the hex address that lspci gave you.  May I suggest entering 'PCI:1:11:0' at the prompt.

---

