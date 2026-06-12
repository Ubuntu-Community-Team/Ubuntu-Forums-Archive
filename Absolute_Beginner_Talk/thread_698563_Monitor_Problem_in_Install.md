---
title: "Monitor Problem in Install"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by brad_lastname on 2008-02-16
Okay, here's my problem. I've tried it with both Ubuntu and Kubuntu disks and I get the same result. I'm trying to run and install on a laptop, when I select Run or Install it goes through the normal loading text and the monitor turns off, not just black, but off and I hear the startup sounds. I tried it with the Ubuntu disk on Start in Safe Graphics mode and it goes black, not off, and again the startup sounds. I have a vague and limited idea about drivers and such, but I'm completely lost here. 

Any help would be greatly appreciated, I'm looking forward to one day living free of windows.

---

### Post by dstew on 2008-02-16
Do you know that the CD is OK? Check the CD integrity. If the disk is OK, then your problem probably has to do with the Live CD system not interacting with your hardware correctly. Usually, it is with the video display, but it can also be a problem with the advanced programmable interrupt controller (APIC) or the advanced configuration and power interface (ACPI).

You can control how the kernel interacts with these systems at boot time by adding parameters to the kernel line. To do this, press F6 at the first screen. Select the kernel line, and try adding these parameters to it:```
noapic nolapic acpi=off
```
If you are still having problems, try installing using the Alternate Install CD. It installs the same Ubuntu system, but uses a text-based installer that is gentler on your system. You can get it from the same[ Ubuntu Download page]("http://www.ubuntu.com/getubuntu/download"). Check the box below the Start Download button.

---

### Post by brad_lastname on 2008-02-17
Okay, I tried that. Just to make sure, I hit F6 on the first screen, added that code to the end of the line and hit enter. It ran, but I got the same result. Any ideas?

---

### Post by dstew on 2008-02-17
Try the Alternate Install CD.

---

