---
title: "Xubuntu 6.10 not recognising network card"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Paqman on 2007-03-26
I'm just installing Xubuntu 6.10 on an old PC from down the back of the cupboard. Installation with the alternate CD went fine, except that it did not recognise the onboard ethernet during installation.

So now the machine can't see the router. No eth0 device showing in network settings. Can someone point me in the right direction to get this device up and running? Thanks!

---

### Post by overdrank on 2007-03-26
> **Paqman said:**
> I'm just installing Xubuntu 6.10 on an old PC from down the back of the cupboard. Installation with the alternate CD went fine, except that it did not recognise the onboard ethernet during installation.

So now the machine can't see the router. No eth0 device showing in network settings. Can someone point me in the right direction to get this device up and running? Thanks!

Hi and welcome. Well for starter can you tell us what kind of network card that it is? If you can go to the terminal and type in the command lspci that should tell you the type of network card. Then someone can help find the solution. Good luck!

---

### Post by Paqman on 2007-03-26
Sorry, the term "card" in the title was a bit misleading. It's onboard, not PCI.

---

### Post by chili555 on 2007-03-26
Nonetheless, the command lspci will give us its particulars. We need everything you can find about your Ethernet Controller.

---

### Post by Paqman on 2007-03-26
Righto, here you go:
```

xubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

```

---

### Post by chili555 on 2007-03-26
Wow! Nothing. Zip-o-la.

Is this a commercially purchased computer or a home-built? Tell us everything you can about it. Brand, model, etc. If you feel a bit adventuresome, you might open the case and get your brightest flashlight and strongest glasses and see if you can determine the make and model of motherboard.

Is the ethernet connection enabled in the BIOS?

There are wonderful add-in PCI ethernet adapters available at [www.newegg,com](www.newegg,com).

---

### Post by Kobalt on 2007-03-26
Do you have an output when you type 
```
lspci | grep -i ethernet
```
?

---

### Post by Paqman on 2007-03-26
Ah, how embarrassing. Indeed, somebody had turned the ethernet off in the BIOS at some point. I've turned it back on and now we have:
```

xubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
**00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)**
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

```

Since this is a fresh install i'm tempted just to re-install now that the BIOS is correct. Unless this is easily fixed of course...

---

### Post by Paqman on 2007-03-26
Ok, scrub my last. After a reboot and twiddling the network settings to make it play nicely with the router it's working fine.

Which just leaves me wondering: why the hell did anyone turn the networking off in the BIOS?

---

### Post by Kobalt on 2007-03-26
Good question indeed !
Is someone mad at you at home ? ;)

---

### Post by chili555 on 2007-03-26
I see it's a 440BX-based motherboard. Pretty old machine. There's nothing wrong with that, linux is perfect for old hardware and saves a few machines from the dumpster. However, if the CMOS battery is a bit tired, I wonder if the BIOS may have defaulted back to factory defaults.

---

### Post by Paqman on 2007-03-26
Possibly, it was in the back of the cupboard for a long while. It was originally a business machine though, so having ethernet disabled seems pretty weird.

Xubuntu is running pretty well on it, especially considering the mighty (*cough*) 96MB of RAM. I'd now definitely recommend Linux for people wanting a cheap way to get surfing and emailing. Machines like this one can be picked up for next to nothing.

Man, how heavy and bulky are those old CRT monitors though? I nearly herniated myself lugging it from the hall cupboard to the lounge.

---

### Post by tc10b on 2007-03-26
They are heavy, but it relies on good old fashioned manual handling. a.k.a getting someone else to help. :)

---

