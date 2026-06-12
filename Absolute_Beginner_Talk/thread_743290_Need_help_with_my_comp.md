---
title: "Need help with my comp"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by jprice19 on 2008-04-02
I downloaded Ubuntu on to a cd and put it on my old computer. I then got a new computer and tried to use the same CD, but for some reason I can't get it to work. It starts booting and then freezes and won't do anything. Do I just need to wait? Will it work with my comp? Here's the specs

Sony VAIO FZ Series VGN-FZ260E/B Notebook Computer 
 • 2GHz Intel Core 2 Duo Processor T7250 CPU  • 2GB (2x1GB) RAM  • 250GB 4200rpm SATA Hard Drive  • Blu-ray ROM/DVD-RW Combo Drive  • nVIDIA GeForce 8400M GT Graphics  • 15.4" Widescreen Display  • 802.11a/b/g/n Wi-Fi

---

### Post by jprice19 on 2008-04-02
please help

---

### Post by saj0577 on 2008-04-02
Should work just give it time.

Please try to use better thread titles next time.

Thanks
Saj

---

### Post by NightwishFan on 2008-04-02
Highlight start Ubuntu, and press f6. Add:
```
noacpi
```
at the end and delete
```
quiet splash
```
and see where the boot hangs.

---

### Post by jprice19 on 2008-04-02
thank ya'll very much. I really appreciate it

---

### Post by jesusfreak107 on 2008-04-02
yes, delete > quier splash and see how far you get. 
Questions:
 Is is a 64bit machine?  If so, download the 64 bit version.
does the message say "kernel panic" when you delete "quiet splash"?  if so, add > boot:linux pci:nosort to the end, and maybe > text at the end of that, if it does not work.

Nice computer!  oh, and one other thing:  "old computer." if this computer was running any version below 7.10,  I would reccomend downloading it from the website again, to make sure you have the latest version.

---

