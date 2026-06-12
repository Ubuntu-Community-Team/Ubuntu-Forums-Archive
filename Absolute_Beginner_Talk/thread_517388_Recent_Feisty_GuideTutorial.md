---
title: "Recent Feisty Guide/Tutorial"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by paneas13 on 2007-08-04
I am looking for any recent guide on how to install Feisty. I am saying "recent" due to Feisty's critical bugs. e.g. Should I add the --no apic-- option into the kernel line of grub ? Should I fix the hdd problem ? Shoud I face any nvidia 8700 drivers problem ? 

I guess that you understant what I mean. All the tutorials I found are about the typical blah-blah next-to-finish instructions.

Anyway, could you tell what I should notice? I am going to install Feisty on the following Friday. I mean, which are the problems nowadays....

---

### Post by Doberman92 on 2007-08-04
Some of the problems during install? You might burn the image incorrectly as a data CD and not a .iso file. Other than that, I've heard sometimes it doesn't detect the monitor sometimes, sometimes the x server doesn't install correctly, and some occasional problems with Nvidia, although for the most part, just resolution problems, which can be fixed easily. Oh, and some wireless cards won't work off the bat. Any problem you might have, I'm sure someone on the forums has an answer.

---

### Post by wolfen69 on 2007-08-04
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)  is a good place to start.

---

### Post by aysiu on 2007-08-04
What critical bugs are you talking about?

The Feisty .ISO you download now is the same one that was available in April, when Feisty was released. Patches and updates come *after* you install Feisty. So all the "old" Feisty guides should still apply.

---

### Post by MrFSL on 2007-08-04
> I am saying "recent" due to Feisty's critical bugs. e.g. Should I add the --no apic-- option into the kernel line of grub

First off... what are you talking about? Critical Bugs? 

As far as the "no apic" flag, APIC or "Advanced Programmable Interrupt Controller," and its use should be based on your hardware. If you have older hardware, proprietary hardware, or buggy hardware you can use the flags:
```
no apic no lapic
```
to correctly disable this feature. For more information on APIC [CLICK HERE.]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture")

---

### Post by paneas13 on 2007-08-05
First of all, thank you very much for your answers.
Saying "critical" bugs, I mean these that trouble the beginners mainstream. Such as, if you have the latest nForce chipset you cannot boot normally. You have to add a noapic option,or something like that. Althought, I've heard that there is/was some kind of incompatibility between the latest DX10 nVidia 8*** cards. I do not know if there are more, but I can say that the Feisty version was more buggy than the Dapper one. The hard drive bug which I read in the LinuxFormatMagazine, was about WD HDD that occurs damage or even kill this device. I do not remember much stuff, so I think that you might guide me what bug or fixes should I patch first.

Thank you guys!

---

