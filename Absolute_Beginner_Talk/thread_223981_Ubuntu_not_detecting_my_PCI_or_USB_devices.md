---
title: "Ubuntu not detecting my PCI or USB devices"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by noham on 2006-07-27
I made the decision recently to switch over from Windows XP to Ubuntu.  The install seemed to go smoothly and it boots fine but it seems that none of my PCI or USB devices are being detected by Ubuntu.

When I type sudo lspci, it just goes straight to the next line - no entries appear.  The same goes for when I type lsusb.  I've tried reinstalling Ubuntu once already and that made no difference either.  The computer is not able to detect my wireless PCI card, my USB thumb drive, my printer or any of my other devices that were working fine in Windows XP.  Is there some basic step that I'm missing to activate my PCI and USB devices?

My hard drive and cd-rom drives are detected fine.  Also, my graphics card seems to be work as well (its an AGP card).

Thanks for the help, Ubuntu seems like a great system and I'd love to get it up and running.  If I can at least get it to detect my wireless card, I'm sure I can get the rest of it setup without too much difficulty.

Thanks!

---

### Post by GuitarHero on 2006-07-27
It may be that some of your chipset/usb drivers were not installed.  Look in the device manager and see if there are any unknown entries.

---

### Post by justicerulesok on 2006-07-27
please don't think I'm being patronising as I'm only a n00b myself, but have you installed the drivers etc for these things?  Have you set up a printer 'system' 'administration' 'printing' there are also know issues with wireless devices (not known issue as in micrsofts - its b*G*r*d it''l never work so deal with it, but more in a you have to search, learn, fiddle & fumble & then it will be perfect sence).

If you have tried these thing - I'm sorry, my bad :-(
If not there are plent of people here to help you & your problems wont last long :-)

Good luck,
Justice.

---

### Post by noham on 2006-07-27
I've tried installing the drivers, for instance, for my wireless network card.  The driver itself installs fine, but it doesn't connect with any hardware.  From what I understand, when I type lspci it should show all pci devices - because it doesn't return anything I assume that Ubuntu is not recognizing my PCI bus or cards.

I've also tried inserting my USB thumb drive and nothing happens.  I would think that the system should automatically detect this, right?  

I haven't installed anything after the basic installation except ndiswrapper.  Do I have to manually install the drivers for my PCI Bus and USB ports?

As for the other question about unrecognied hardware, I'm not sure.  When I look at the device manager it doesn't explicitly say anything is unrecognized.  How can I tell if something is recogned or not?

Thanks for the help!

---

### Post by noham on 2006-07-27
So, I don't seem to be getting many responses, so I figured I would add some more info to try and illicit some help.

Anyway, Ubuntu still doesn't seem to be recognizing my USB outlets and PCI cards.  I checked the device manager and the only that I can see, which may be my wireless card is an entry called:
"16550A - compatible COM port"  

It lists it as a serial device in the info, but I think thats because Ubuntu is just misrecognizing the hardware.

Also, when I start up the computer it says that PCMCIA is not present.  Could this be part of the problem?

Thanks for the help!

---

### Post by Malac on 2006-07-27
I don't know as you didn't say what the motherboard was but;
It may be your motherboard/bus/chipset/something is not being correctly recognised so not being setup properly.
Try seeing if there are any references to your motherboard in bug reports or the wiki perhaps there is a motherboard driver you need to install first.

Hope this helps.

---

### Post by noham on 2006-07-27
According to lshw my motherboard is MS-6366, Micro-Star International.

Also, when I type dmesg I get a long string of text.  I can't post the entire text because that computer doesn't currently have access to the internet, but some of what I think might be important is:

PnPBios: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing

PCI: Bridge: 0000:00:01.0
     IO window: disabled
     MEM window: dc000000-ddffffff
     PREFETCH window: dc000000-ddffffff

"pci=routeirq"

isapnp: No Plug & Play device found


Does any of this help?

Thanks!

---

### Post by noham on 2006-07-30
***bump***

If someone could offer me some more help I would really appreciate it.

Thanks!!!!!!!!!

---

