---
title: "Sound card not working"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by JW_00000 on 2006-01-17
Hello,

I installed Ubuntu some time ago, but my soundcard is not working. The problem is I don't know the type or brand, so I can't search a driver for it. I looked in the Device Manager, but there are some devices I don't recognize, my sound card is probably one of them. Is there a way I can get the brand and type, and a driver?

---

### Post by christhemonkey on 2006-01-17
In a terminal;
lspci
this should give a list of devices that are PCI, which one of will be your sound card?
let me know if this helps!

---

### Post by az on 2006-01-17
How old is the computer?

---

### Post by JW_00000 on 2006-01-17
lspci returns the following
```

$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0e.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) PCI0680 Ultra ATA-133 Host Controller (rev 02)
0000:00:10.0 Serial controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

```
I think it's "Silicon Image, Inc. (formerly CMD Technology Inc) PCI0680 Ultra ATA-133 Host Controller", but I don't know for sure...
The computer is around five years old, it's a Pentium II with 350 MHz, so quite old...

---

### Post by christhemonkey on 2006-01-17
Its a RAID controller, so id say its probably not your sound card.

---

### Post by az on 2006-01-17
[QUOTE=JW_00000]lspci returns the following
```

$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0e.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) PCI0680 Ultra ATA-133 Host Controller (rev 02)
0000:00:10.0 Serial controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

```
I think it's "Silicon Image, Inc. (formerly CMD Technology Inc) PCI0680 Ultra ATA-133 Host Controller", but I don't know for sure...
The computer is around five years old, it's a Pentium II with 350 MHz, so quite old...[/QUOTE]

There is no sound card listed here.  Maybe it is disabled in your bios?  Boot into the bios menu (before it loads the os) and play around.

Then, look at the wiki page about old sound cards... 

[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

---

### Post by JW_00000 on 2006-01-18
I opened my computer case, and the outputs are connected with my motherboard, so I don't have a PCI sound card. My computer is a (Fujitsu-?)Siemens Xpert, and on their site I found some drivers, but I can't seem to find the right one. Most of them also seem to be only for Windows.

---

### Post by az on 2006-01-18
[QUOTE=JW_00000]I opened my computer case, and the outputs are connected with my motherboard, so I don't have a PCI sound card. My computer is a (Fujitsu-?)Siemens Xpert, and on their site I found some drivers, but I can't seem to find the right one. Most of them also seem to be only for Windows.[/QUOTE]
If you can tell which chip is the sound chip, post what is written on it.  If you can find the specs for your motherboard, post the type of sound chipset.

---

### Post by Optiker on 2006-01-18
If you are dual booting with Windows, you may be more comfortable getting that information from Windows than from Linux or the BIOS setup...

This is the process for Windows XP, but it should be pretty simlar for other versions.

1. Right-click "My Computer" on the desktop

2. Select "Properties" in the popup menu

3. Select the "Hardware" tab

4. Click the "Device Manager" button

5. find the line that says "Sound, video and game controllers" If it has a + sign at the left of the line, click on the + sign to expand the listing. If it has a minus sign, it should already be expanded with a list of devices.

6. In the expanded list, find the line that describes your sound deveice, for example, "SoundMAX Integrated Digital Audio" in my off-the-shelf Dell running Windows XP.

7. Right-click on that line will open a window with additional information.

Optiker

---

### Post by JW_00000 on 2006-01-18
My motherboard is a V65MA or V66XA from Siemens, I didn't found the sound chipset, so its type I don't know. I found the documentation of the board online and at home, and it mentions a "3-D audio solution" and an "onboard 3-D video controller", but no type.
I'm soory, but I don't have a dualboot...
Is there something else I can do? Maybe is there some application that can detect it?

---

### Post by christhemonkey on 2006-01-19
I couldnt find any documentation on it online?

---

### Post by bscbrit on 2006-01-19
According to this site:

[http://www.softwareandstuff.com/h_dsk_acervm65.html](http://www.softwareandstuff.com/h_dsk_acervm65.html)

the sound hardware is:

Crystal CS4235 16-bit audio with 3D stereo sound

hope this helps somebody - I know very little about configuring sound cards!:(

---

### Post by az on 2006-01-19
[http://www.softwareandstuff.com/h_mb_acervm65.html](http://www.softwareandstuff.com/h_mb_acervm65.html)

Sound Crystal CS4235 16-bit audio with 3D stereo sound 



[http://www.uktsupport.co.uk/acer/mb/acv65ma.htm](http://www.uktsupport.co.uk/acer/mb/acv65ma.htm)

CN20 Audio connector (for CS4610 adapter card) 


Try the snd-cs4236 module.


Or try the snd-cs46xx one.

Use this:
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

---

### Post by Vladimirm on 2006-01-19
do you have two soundcards? one built into your motherboard? and anotehr one?

---

### Post by JW_00000 on 2006-01-20
Yay! :p It's working! First I thought it wasn't, but after I changed to a higher volume, I heard it! Thanks for all the support, I thought I wouldn't be able to solve this, but the community is great. You even looked up the sound chipset in my motherboard. Thanks! :smile:

---

