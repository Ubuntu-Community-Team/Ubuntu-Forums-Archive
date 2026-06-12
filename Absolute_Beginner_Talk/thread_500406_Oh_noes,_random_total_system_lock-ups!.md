---
title: "Oh noes, random total system lock-ups!"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-07-13
I sometimes get odd moments of ALMOST lock-ups in CS and CS:S. Then finally, worst comes to worst and it happens. I even locked up in Firefox, which leads me to believe it isn't graphics related.

I need a program to tell me what temperature my PC is running at, I have a slight inkling that it is overheating, or maybe you guys have another idea? :( It only has happens after gaming for a long time.

---

### Post by Alex&amp;Linux on 2007-07-13
Well, is your system becoming.....exceedingly hot?
Perhaps its memory leak? (graphics card)

---

### Post by Megatog615 on 2007-07-13
This happens USUALLY when your system is getting too hot, or your hardware is broken somehow.

---

### Post by kavon89 on 2007-07-13
What thing should I search for in the Package Manager to check or monitor my system temperatures? Got any easy to install programs you can link me to if none are in the repository?

---

### Post by Alex&amp;Linux on 2007-07-13
Dont personally know of anything in that regard, however, your BIOS should allow access to fan reaction sensitivity and RPMs, other junk like that.
Perhaps there youll find the solution.

---

### Post by tgalati4 on 2007-07-13
sudo apt-get install lm-sensors

Search the forums for how to set up.

---

### Post by kavon89 on 2007-07-14
```
kavon@kavon-ubuntu:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +52°C

```

Seems accurate, while overclocking my cpu, my BIOS reported a low ~ 50C temp... but SpeedFan in Winblows reported ~47C, both idling. I thought maybe the BIOS was wrong.

I am expecting a 55-56C temp when under load (gaming) and I'll test that tomorrow since it is midnight and I'm too sleepy for a few hours of gaming. ;) . It is possible that CS/CSS under wine is causing some extra stress and bringing the temps high, I will become worried if it reaches 58 or more.

Any way I can get that sensor command's result tempature updated every so often and displayed next to the date? I might take a crack at it and write my own little plug-in for it, I could base it off of another program's icon tray code since things are open source. :o

---

