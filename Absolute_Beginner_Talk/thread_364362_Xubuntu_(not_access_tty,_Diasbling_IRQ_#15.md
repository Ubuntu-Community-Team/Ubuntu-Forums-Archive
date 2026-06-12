---
title: "Xubuntu (not access tty, Diasbling IRQ #15"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by simonfoley on 2007-02-18
Dear All

I am trying to to get rid of XP on an old Acer TravelMate 210T (Celeron 700 MHz, 256 Ram).  I would really like to replace this with Xubuntu as XP is simply too slow and my gf only needs it for reading mail.

I installed Ubuntu last week on my main computer, although to be frank, I do not really know enough about linux to get too far with it, although i can set up the basics.

Anyway, I made the burned the Live CD for Xubuntu and started the install and then I get

**'can't access tty'**

Then I get a list of repeated messages that read

**Disabling IRQ #15**

**irq 15; nobody cared (try booting with the "irqpoll" option handlers) **

I found the following on the'net from a linux site

[I]    * ALi 1553 PCI/AGP/UDMA-ATA/USB/Audio integrated chipset.
    * ATI Rage Mobility M graphics chipset with 4MB SGRAM.
    * Lucent LU'97 software modem.
    * Floppy disk drive.
    * Twin PCMCIA slots.
    * Two USB ports.
    * Serial port.
    * Parallel port.
    * PS/2 mouse port.
    * Synaptics mousepad with scrolling rocker switch.
[/I]

This just repeats on and on.

I would really like to be able to use this laptop for this.

I think it may be that the motherboard or CD is not compatiable in which case, there is nothing to do.

Simon

---

### Post by solar george on 2007-02-18
Have you verified the install cd (use the check cd for defects option on the menu)

If this fails you need to burn the cd again.

Make sure that you burn it at a low speed

---

### Post by simonfoley on 2007-02-20
I have tried this and it is not a disk issue as I tried my normal Ubuntu disk also and got the same result

---

### Post by simonfoley on 2007-02-20
Please if anyone can help me, I would be most appreciative.

I did a search on **/bin/sh: can't access tty; Job Control Turned Off** and as you can tell this is a problem many, people are having and there seems to be no answer for this.  I have tried to disable whatever I can in the Bios to no effect.  

I get the message and then a prompt that is IS (imitramfs).  I can only access the help commands and then it goes through a loop giving the message
[B]
[17179829.316000] irq 15: npbody cared (try booting with the "irqpoll" option)
[17179829.316000] handlers[/B] and then it tries to disable these.

I would really like to be able to install this as I would like to get away from Windows and into Linux but this is one big step to get over :confused: 

Simon

---

### Post by meborc on 2007-02-20
what version xubuntu are you trying to install? if you downloaded the daily image of feisty, then it just might be a bad iso... feisty is due in april...

i would suggest you download Xubuntu 6.10 (edgy eft) Alternate CD - it does not give you the live cd, but the terminal install...

EDIT: try this site - [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by Brendantb on 2007-02-20
Hi, 

I am new to Linux myself, so I can only be of limited help: 

"/bin/sh: can't access tty; Job Control Turned Off" is a non-specific warning given when the installation can't proceed; there isn't just one cause for it, so it's not so helpful. 

I had difficulty installing on a similarly specced machine to yours, and at one point saw a similar "nobody cared" warning. 

I was able to solve my problem by booting the alternate CD, in text mode. It isn't that much harder than the live CD.

---

### Post by dmatrix on 2007-02-21
A buddy of mine has the exact same laptop, wanting to do the exact same thing, install Xubuntu on it and rid himself of the windows install on it. The problem is the irq 15, nobody cared error. Booting with the irqpoll option in grub makes it boot, but then for some reason the pcmcia card does not work, therefore no wireless. Any other ideas to try would be great.

---

### Post by simonfoley on 2007-02-21
*I was able to solve my problem by booting the alternate CD, in text mode. It isn't that much harder than the live CD.*

I tried this today.  Downloaded and burnt another CD and I am getting the same problem again.  Hmmm.

Where next?  Do I give up and just assume that xubuntu can not work on my PC?

I really want to install it but.....

Simon

---

### Post by dmatrix on 2007-02-21
Well I have tried xubuntu, normal ubuntu and knoppix as well. On this laptop all of them complain about irq 15 problems, that no one cares about. I tried all sorts of boot options, with some of the options I could get rid of the irq 15 problems, but the pcmcia slot would still complain about irq conflicts when trying to load the drivers for the pcmcia network cards. Other options would hang at the point when the cd drive was detected.

Finally on Knoppix I tried with these options: acpi=off noapic pci=bios

No errors this time, but the pcmcia cards still do not work. I tried to unload/load the drivers with modprobe and same results. So basically this laptop is useless as I cannot use a pcmcia card on it, be it wired or wireless. btw. the Windows install on this laptop the pcmcia cards work just fine. There are no bios options to change the irqs either.

---

### Post by simonfoley on 2007-02-22
Should I change this title to 'thinking of giving up on Xubuntu'?

S

---

### Post by r_duke on 2007-03-01
Hi,
I had the same problem. I could bypass it by booting the CD with the [COLOR="Blue"]-- irqpoll[/COLOR] option (as recommended). when booting, press F6 and add the irqpoll command behind the command line that is already there. i got passed the error but then the install halted when loading the X interface. 

I tried Knoppix and had the same error. [COLOR="blue"]-- irqpoll [/COLOR]resolved the problem there and the OS loaded without errors. it seems that this is not an ubuntu only problem..
hope it helps
cheers
r_duke

---

### Post by simonfoley on 2007-03-04
Wow, that worked and even though I am now struggling with my wireless card, I have now managed to get an installation working.  Thanks for your help with this and I hope others with the same issue can get this up and running.

Simon

---

