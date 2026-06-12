---
title: "Absymal slowness in Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by vnt87 on 2007-04-21
I just finished upgrading to Ubuntu Feisty a couple of hours ago. The first time I reboot after that Ubuntu hanged at the bootsplash screen. After I reset the machine I got to the desktop normally, but it runs rather slow, much slower than my Edgy actually, I know it's not supposed to be like this.
Firefox has the most tremendous slowdown, it takes up to 20 seconds to open up, and another 10 seconds to open a new tab. Also, it almost hangs every time I try loading a heavy webpage.
Something is not right. Does anybody out there experiencing similar problem? Could this be because I'm not using the default Human theme? Or do I need to install the official driver for my graphic card (ATI Radeon 9600XT). Just thinking about that because the way Ubuntu is running right now reminds me of Windows when it doesn't have  a proper graphic card driver installed.

---

### Post by SnotRocket on 2007-04-21
Opening a program is much more memory and processor intensive than GPU, can you post your system specs in total?

---

### Post by vnt87 on 2007-04-21
I got a Intel Pentium 4 - 2.66 GHz with 512MB of RAM, and an ATI Radeon 9600XT. While I think this is obsolete, I still think it is capable of running Feisty. I was able to put XP and Edgy on this machine and they both ran smoothly.

---

### Post by kittyhawk63 on 2007-04-22
> **vnt87 said:**
> I got a Intel Pentium 4 - 2.66 GHz with 512MB of RAM, and an ATI Radeon 9600XT. While I think this is obsolete, I still think it is capable of running Feisty. I was able to put XP and Edgy on this machine and they both ran smoothly.

What video driver are you using? ATI?  fglrx?  Vesa? other?
Have you tried installing the official ATI driver from:
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

kh

---

### Post by vnt87 on 2007-04-22
> **kittyhawk63 said:**
> What video driver are you using? ATI?  fglrx?  Vesa? other?
Have you tried installing the official ATI driver from:
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

kh

Thanks, I was thinking of installing the official fglrx, but I had bad experience with it before, so I was reluctant to try it again.
I just grabbed the latest 8.36.5 from their website, and install by following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") with some regards to make the change from 'Edgy' to 'Feisty'. Despite the kernel module failed to compile, it *appears* to have done the trick. Firefox loads much faster now, as do most other programs.
Thanks for the suggestion, I'll hit this thread back if something bad came up again.

---

### Post by th3james on 2007-04-22
Hi
I have very similar spec to yours, (p4 2.6, 512mb ram..) but i have an nvidia mx440. Feisty's speed seems inconsistent, certain tasks are relatively quick, but certain programs run very slowly (especially eclipse, which runs insanely slow), and some random tasks take ages. When the 'slowness' occurs, the CPU usage hits 100% for the duration of the task then drops back down. I've tried using both the open source driver and the nvidia 1 for my card, and have also used beryl and not used beryl, the slowness is the same regardless

EDIT: edgy and dapper never had this issue on this machine

any ideas?
thanx, th3james

---

