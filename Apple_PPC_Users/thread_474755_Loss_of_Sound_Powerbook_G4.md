---
title: "Loss of Sound Powerbook G4"
date: 2007-06-15
forum: Apple PPC Users
---

### Post by czechman86 on 2007-06-15
I have been running Ubuntu fine, with everything working for about a week now, and then today when I booted my machine up, there was no sound. I followed the guide in the FAQ for PPC, and found that I was missing nothing in regards to what should have been installed. How can i regain sound? Thank you!

Edit:
I have also tried restarting the machine, which resulted in no change; still no sound.

---

### Post by ssam on 2007-06-15
can you run
```
cat /proc/cpuinfo
```
in a terminal and post the output?

it is probably [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

the current work around is to install a edgy kernel. ask if you need help doing this

---

### Post by czechman86 on 2007-06-16
```
processor       : 0
cpu             : 7447A, altivec supported
clock           : 749.999000MHz
revision        : 0.1 (pvr 8003 0101)
bogomips        : 36.73
timebase        : 18432000
platform        : PowerMac
machine         : PowerBook5,4
motherboard     : PowerBook5,4 MacRISC3 Power Macintosh 
detected as     : 287 (PowerBook G4 15")
pmac flags      : 0000001b
L2 cache        : 512K unified
pmac-generation : NewWorld
```

I do not know what to make of this. If i need to install the edgy kernel, please let me know, and I am very new to linux, so I will need help with it. Thanks again!

---

### Post by ssam on 2007-06-16
thanks. that seems to be an aluminium powerbook, so i dont think it should suffer from the above bug.

The problem might just be that the sound module is not loaded at boot time. to fix this you just need to add a line to a text file.

press Alt+F2 to get a run program box. (alt is the same as option key)

copy the following into the box

```
gksu gedit /etc/modules
```

now add the line
```
snd-powermac
```

to the bottom of the file.

save it and reboot the computer.

---

### Post by czechman86 on 2007-06-17
added em and now it works! Dekuju Moc!

---

