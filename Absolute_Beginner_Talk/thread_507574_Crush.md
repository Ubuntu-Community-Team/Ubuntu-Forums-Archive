---
title: "Crush"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by xwhisper on 2007-07-23
I have some very strange problem:
After I install Ubuntu (tested with 6.10 and bellow) it runs only for about half an hour and then completely freezes (the whole system, not only the X). After I restart it runs again but  for shorter time and then freezes again. After several restarts and the system is completely dead. I have Fedora Core 4 and it runs perfectly, but my PC obviously have some problem with Debian based installations (tested and with Debian). Sometimes when I try to reinstall it even the installer crushes for no reason. A friend of mine told me that it's probably incompatable kernel. I cannot read system logs cause my system does not live long enough after the crush to go to that directory. Can somebody help me? Is there a Ubuntu with RedHat based kernel to try it? I'm sorry but my PC is now far away and can't use it right now.

AMD K6-2+ 500MHz
SiS 530 8MB Video
356 MB SDRAM
(can't run movies on that thing)

---

### Post by ddrichardson on 2007-07-23
This sounds like overheating, which k6-2's were awful for. There may be something configured in the kernel causing this, but more likely its something in the fedora based kernel preventing it.

In the BIOS for most K6-2 chips you could control the clock speed, a lot of these chips are actually rated at 475 MHz - try that and see if it gives you the stability to compile a custom kernel.

---

### Post by xwhisper on 2007-07-24
Hmmm, sounds reasonable...
I'll try it as soon as I can!:)

---

