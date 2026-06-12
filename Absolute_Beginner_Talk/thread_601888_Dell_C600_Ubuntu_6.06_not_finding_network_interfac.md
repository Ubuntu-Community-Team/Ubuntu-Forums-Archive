---
title: "Dell C600 Ubuntu 6.06 not finding network interfaces"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by vildrik on 2007-11-03
I've installed ubuntu 6.06 on a dell c600 laptop with what I believe is a 3com 3c556 Hurricane ethernet card (If anyone knows how to find out exactly what it is, that may help). During the installation process it can't find network interfaces. I get this error message:

```
[!] Detect network hardware
No Ethernet card was detected, but a FireWire interface is present. It's possible, though unlikely, that with the right FireWire hardware connected to it, this could be your primary Ethernet interface.
Do you intend to use FireWire Ethernet?
```

Whether I say yes or no to this question, it brings me to this error message:

```
[!] Configure the network
No network interfaces detected
No network interfaces were found. The installation system was unable to find a network device.
You may need to load a specific module for your network card, if you have one. For this, go back to the network hardware detection step.
```

I get no more error messages throughout the rest of the installation process, but when I open the network settings dialog all i see is the modem connection ppp. I'd like to get a wired ethernet connection going.

Thanks in advance for any help.

---

### Post by overdrank on 2007-11-03
> **vildrik said:**
> I've installed ubuntu 6.06 on a dell c600 laptop with what I believe is a 3com 3c556 Hurricane ethernet card (If anyone knows how to find out exactly what it is, that may help). During the installation process it can't find network interfaces. I get this error message:

```
[!] Detect network hardware
No Ethernet card was detected, but a FireWire interface is present. It's possible, though unlikely, that with the right FireWire hardware connected to it, this could be your primary Ethernet interface.
Do you intend to use FireWire Ethernet?
```

Whether I say yes or no to this question, it brings me to this error message:

```
[!] Configure the network
No network interfaces detected
No network interfaces were found. The installation system was unable to find a network device.
You may need to load a specific module for your network card, if you have one. For this, go back to the network hardware detection step.
```

I get no more error messages throughout the rest of the installation process, but when I open the network settings dialog all i see is the modem connection ppp. I'd like to get a wired ethernet connection going.

Thanks in advance for any help.

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by vildrik on 2007-11-03
```
lspci

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:03.0 CardBus bridge: Texas Instruments PCI1420
0000:00:03.1 CardBus bridge: Texas Instruments PCI1420
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
```

---

### Post by vildrik on 2007-11-04
Anyone got any ideas?

---

### Post by overdrank on 2007-11-04
> **vildrik said:**
> Anyone got any ideas?

HI, ( I am no networking expert)  the card is not detected, was it inserted when you ran the command? The only thing I could find on that card 
[http://ubuntuforums.org/showthread.php?t=366484&highlight=3com+3c556+Hurricane+ethernet+card](http://ubuntuforums.org/showthread.php?t=366484&highlight=3com+3c556+Hurricane+ethernet+card)
You may try the live cd of Feisty
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

---

### Post by vildrik on 2007-11-05
Well, it is a laptop, so everything should still be plugged in and running correctly. I guess I could try installing windows on it to make sure the ethernet card's still working correctly.

I've already tried the livecd on it and it didn't work too well. There's a few problems with it: The installation window doesn't fit on the screen, as it runs in 800x600, the cd drive is very slow, and I don't have much RAM or processor speed so the whole process takes forever and freezes up quite easily. I think my laptop may just be too old for this...

---

### Post by bremen on 2007-11-05
There is no ethernet card listed in lspci so I believe it may be missing.  If you flip the laptop over and remove the bottom hatch you should be able to visually verify whether you have it or not.  Mine is wrapped in some white paper with a bunch of certifications on it. (Dell Latitude C600)

As for your problems with the installation program just remove the top and bottom panels and you should have enough room for the installation program.  Also you should probably consider running xubuntu instead.

---

### Post by SunnyRabbiera on 2007-11-05
you might want to try a later version of ubuntu as even though dapper is LTS and stable it probably wont cover as many drivers.

---

### Post by chemtut on 2007-11-05
Do you have a card slot?
If so buy a pcia (?) ethernet card--in the UK they are about £10
that should solve the problem
good luck

---

### Post by vildrik on 2007-11-05
I decided to try installing 7.10 and then get a wireless connection going. I do have a pcmcia slot and a wireless card. Hopefully that'll go smoother.

Thanks for all the help.

---

### Post by vildrik on 2007-11-06
Well that worked just fine, damn i love this operating system.

---

