---
title: "PowerBook G4 no display"
date: 2010-05-03
forum: Apple Hardware Users
---

### Post by rixanonna on 2010-05-03
im installing ubuntu 10.04 for ppc on a mac powerbook g4 1.67ghz. half the time it boots up to openfirmware, half the time it boots correctly.
after install, no display would come up, so i changed the /etc/init/rc-sysinit.conf to boot to runlevel 1. selecting the failsafe x doesn't boot, and though im sure ubuntu is a nice distro, im not familiar with how to configure x. at runlevel 1, i did Xorg -configure to create a xorg.conf file moved it to /etc/X11/, thinking i could reduce the resolution with nano. every time i use an example xorg.conf it gives me no screens found, probably because i messed up the edit. the ubuntu live cd has sound, display, and gives me a dialog to install the wireless bcm43xx, though i haven't connected it to the internet and installed it. how can i get the display to work?

---

### Post by linuxopjemac on 2010-05-03
What is the exact model ?

---

### Post by yokohama1970 on 2010-05-30
Same issue as well. Since I have an a1286 MBP running Mac OS 10.6.3, I decided to use my a1106 PB G4 to run Ubuntu 10.04 LTS. I was using Xubuntu 9.04 on my PS3, but I really just like to watch Movies & play Games on it. 

Specs: 1.67 Power PC
1.5gb PC2700 DDR Ram
ATI Mobility Radeon 9600 M10 512mb
15" LCD Low-Res
80gb Fujitsu ATA/100 HD 4200rpm

I will try the Live option to edit xorg or gconf

If anyone else with an a1106 is having the same issue let us know please

---

### Post by linuxopjemac on 2010-05-30
have a look [here]("http://mac.linux.be/content/cross-distribution-issues"). If you need help tell me.

---

