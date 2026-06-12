---
title: "Switch sound port"
date: 2014-01-29
forum: Any Other OS
---

### Post by jobeato8 on 2014-01-29
Hi everyone.

I have eOs wich have Ubuntu 12.04 by base. And I have a small issue. Some time ago I broke a phone jack in one of my audio ports. So in result the SOs always assume that port as preferential. In Windows, in Realtek HD software I had an option to change the preferential port. But here in Ubuntu... I don't know what to do and this is the only thing that is making me thinking to return to Windows (and I don't want that! :( )

Here some information of my audio device.

```
*-multimedia             
             descrição: **Audio device**
             produto: **5 Series/3400 Series Chipset High Definition Audio**
             fabricante: **Intel Corporation**
             ID físico: 1b
             informações do barramento: pci@0000:00:1b.0
             versão: 06
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuração: driver=snd_hda_intel latency=0
             recursos: irq:51 memória:f9ff4000-f9ff7fff



```

Thank you very much in advance.

Best regards.

---

### Post by Yellow Pasque on 2014-01-29
Try setting the problematic jack to "not connected" using hdajackretask:
```
sudo apt-get install alsa-tools-gui
hdajackretask
```

---

### Post by Yellow Pasque on 2014-01-29
Oh, on Ubuntu 12.04, you have to get the utility from here: [https://launchpad.net/~diwic/+archive/hda](https://launchpad.net/~diwic/+archive/hda)

---

### Post by jobeato8 on 2014-01-29
Hi, thank you. I installed the PPA and then the alsa tools, but now when I try to open any of installed programs, they won't open... :(

Edit: did another install and finally my sound works!! yuy!!

But is normal to lose some sound quality?... :/

---

### Post by Yellow Pasque on 2014-01-29
When you run the hdajackretask command, what is the output?

---

### Post by jobeato8 on 2014-01-29
Command not found. I followed this instead and it did well. [http://lists.freedesktop.org/archives/pulseaudio-discuss/2011-December/012342.html](http://lists.freedesktop.org/archives/pulseaudio-discuss/2011-December/012342.html) (when I run the last command it shows up a program).

---

### Post by jobeato8 on 2014-01-29
And when I shut down my PC the sound backs to "no sound". :(
Edit: I found the option  to apply the settings on boot. And I think this with equalizer would work fine. Thank you for your help :)

---

### Post by Yellow Pasque on 2014-01-29
Yes, it looks like "hda-jack-retask" changed to "hdajackretask" at some point.

> Thank you for your help
You're welcome.

---

### Post by Bucky Ball on 2014-01-30
*Thread moved to **Other OS/Distro Support**.*

---

