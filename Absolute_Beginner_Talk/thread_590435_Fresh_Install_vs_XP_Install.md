---
title: "Fresh Install vs XP Install"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Quetzal on 2007-10-24
I was curious to know if anyone could give me any information on which method would be better?

I guess the most important thing would be being able to load the network drivers.  I'm tired of having XP crash and reformatted my notebook.  Before I install anything on the notebook I wanted to know which method would be best (easiest to deal with in terms of driver recognition, video, network, etc..)?  A fresh install on the empty notebook or an installation after XP had loaded the drivers for the notebook?

-Quetzal

---

### Post by lazyart on 2007-10-24
XP drivers would do nothing for an Ubuntu install.

---

### Post by shadylookin on 2007-10-24
XP drivers would have no effect on linux, but if you're going to dual boot xp and ubuntu you should install xp first because it will override the linux bootloader(or write over you linux partition) if you install it afterwards

---

### Post by rundee_f on 2007-10-24
Both OS does not depends each other.. If u ever experienced both XP and Ubuntu, i guess u know that Ubuntu can do anything that XP does (and even more!).

I suggest u do dual boot, but only install minor applications that u need but havent compatible on Ubuntu yet.. (e.g. for me : photoshop CS3).. For the rest, i found Ubuntu is outstanding!!

I love to make my friends jealous!! :lolflag:

---

### Post by Quetzal on 2007-10-24
Is there any documentation on the "install with driver update CD" so that I may download the proper drivers for my hardware and not worry about driver issues when Gutsy Gibbon starts up?

Documentation or pointers/suggestions would be appreciated.  I just checked the live CD and it doesn't recognize my network card.

-Quetzal

---

### Post by lazyart on 2007-10-24
The info is [here]("https://wiki.ubuntu.com/Ubiquity/DriverUpdates") but it's geared toward hardware vendors.

What NIC do you have?  You might be able to get a driver for it onto a thumb drive and install it after the OS install in complete.

---

### Post by Quetzal on 2007-10-24
It's Intel PRO/100, I've already done a full install of Ubuntu on notebook, and all i see when i open the network settings is the Modem connection.  I'll do some searches on the Intel driver...seems as a common drive, and someone else must have already encountered this.

But for the most part installing drivers is same as in Windows?

-Quetzal

---

### Post by Quetzal on 2007-10-24
hmm...looked at alot of documentation.  Any help pointing me how to enable my NIC card?

System:

Compaq Presario 2700T Noteboook
1Gig Ram
15 inch SXGA+ display (1400×1050)
SoundMAX integrated audio
Conexant HSFi V92 56k internal modem
Internal 10/100 Ethernet port (Intel PRO/100 VE)
Built-in 8x/4x/24x CD-RW drive
Modular drive bay with 6x DVD drive and floppy drive modules
Synaptics TouchPad with 4-way scroll pad
PCMCIA slot
One (1) IEEE 1394 Firewire port and two (2) USB ports

Thanks your help is appreciated.

-Quetzal

---

### Post by lazyart on 2007-10-25
That's very strange... that card should work out of the box.

Go to the terminal, type 'lspci' and see if there is any mention of the ethernet controller.

---

