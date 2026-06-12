---
title: "hardware support"
date: 2010-11-28
forum: Apple Hardware Users
---

### Post by linuxopjemac on 2010-11-28
We are working on more automatic support for powerpc based Macs. Think about automatic installation of a working xorg.conf file during installation of Linux for example. For this to be developed tool to work, we need hardware information of as many as possible different PPC based Macs.

If you like to help us achieve this challenging goal, do the following:

Install lshw:
```
sudo apt-get install lshw
```

Run lshw
```
sudo lshw > lshw.txt
```

Attach lshw.txt to a thread here, or send it by mail to
jjhdiederen at zonnet dot nl and tell me which exact machine you have by giving me a link in everymac.com

Please, also post your working xorg.conf file as well as your yaboot.conf file...

Thanks for your help!!

---

### Post by ombra on 2010-11-28
I just installed Ubuntu 10.10 on my [Powerbook G4 867]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_867.html").

Attached my lshw.txt

Hope to help

---

### Post by linuxopjemac on 2010-11-28
Thanks, please also post your xorg.conf file, if you use any...

---

### Post by moviemaniac on 2010-11-28
> **linuxopjemac said:**
> Thanks, please also post your xorg.conf file, if you use any...
none is being used

(mm - Ombra's brother ;) )

---

### Post by linuxopjemac on 2010-11-28
You have a nVidia card, so this is your Mac:
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_867_12.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_867_12.html)

---

### Post by linuxopjemac on 2010-11-28
You have an nVidia card, so this is your Mac:
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_867_12.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_867_12.html)

---

### Post by dpny on 2010-11-28
Will do this tonight or tomorrow: have to open up my G5 and switch out the X800 for the FX5200.

---

### Post by dpny on 2010-11-28
lshw.txt and xorg.conf attached.

---

### Post by linuxopjemac on 2010-11-29
Thanks all, we could also use your yaboot.conf files....
DPNY: can you provide me a link in everymac.com please ?

---

### Post by dpny on 2010-11-29
> **linuxopjemac said:**
> Thanks all, we could also use your yaboot.conf files....
DPNY: can you provide me a link in everymac.com please ?

This one: [http://www.everymac.com/systems/apple/powermac_g5/stats/powermac_g5_2.0_dp_2.html](http://www.everymac.com/systems/apple/powermac_g5/stats/powermac_g5_2.0_dp_2.html)

Just for information's sake, this machine--PowerMac 7,3--also has problems loading the windfarm fan sensors.

---

