---
title: "A few questions ;)"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by acadiansteph on 2007-05-08
I have read that Linux OSs are  closed systems by default (as opposed to Windows). I migrated to Ubuntu 7.04 a few weeks ago and have a couple of noob questions: 1: should I worry about viruses, adware, spypare with Ubuntu (most viruses are written for Windows OSs) 2: what about root kits (are Linux OS more susceptible to them) 3: in Firefox, are temporary internet files located in specific files in Ubuntu. If so ,how may I deleted them? 

Windows was my OS for 13 years, so the questions may seem stupid! 

P.S I love Feisty 7.04. Configured my 3d acceleration (direct rendering), configured my Broadcom 4318 wireless card, and watch DVD with Totem. So I"m glad I have gotten them to work.

My firewall is Firestarter and I am seriously thinking using Bastille Linux. After that, I will read up on NAT (network address translation). 

Thank you, Stephane

---

### Post by Cypher on 2007-05-08
You have it backwards, Windows is closed source while Linux is open source. You have access to the Kernel source code and access to many of the applications that run on it. There are anti-virus software available for Linux, but as you've surmised Linux isn't prone to the same kinds of issue that Windows is. 

There is no registry to get hacked in Linux, also as long as you are careful to always use your user account for everything, any system specific task requires either SUDO or root password, so you are more protected here. 

Root kits usually perform their action by modifying your system somehow and by way of Kernel modules or something similar, and for these things you need Root access. So once again, as a regular user you won't be able to do it and thus are protected. 

It always pays to be a little vigilant even if Linux is largely immune to most of the common problems of Windows.

Firefox should saving temporary files in ~/.mozilla/firefox/xxxx.default/Cache where xxxx is some random string.

Welcome to Ubuntu..:)

---

### Post by starcraft.man on 2007-05-08
Just one more note to add to cypher's answer which I think covered everything :)

I still think that people who run any OS (even linux) should be behind a NAT router. Call it an extra security blanket should anything ever become wild and wipe out linux (not likely, but then again look at the zero days in vista :p)

NAT routers basically filter all internet traffic that is directed at your computer. Their greatest (and most under appreciated feature) is to instantly drop you from public internet. This is done because the router makes all your ports appear as if they don't exist (i.e. invisible). They only open the port for specific traffic when you request it, so like when you request a web page or online gaming.

One more note though, if you run programs in WINE (or any other simulation of windows like Cedega or crossover, or even run Windows in a Virtual emulator) do be aware that programs you run under the emulator or virtual machine will be susceptible to viruses if they have specific vulnerabilites, It isn't much of a risk as the viruses will be contained inside the virtual environment.

Thats it, have fun with Ubuntu.

---

### Post by acadiansteph on 2007-05-08
Thank you very much! Glad to be in the Ubuntu community.:)

---

### Post by starcraft.man on 2007-05-08
> **acadiansteph said:**
> Thank you very much! Glad to be in the Ubuntu community.:)

Your very welcome, and YAY!!!! Another canadian convert :D

We must amass a great Canadian army of Ubuntu/Linux users!!!!

---

### Post by Cypher on 2007-05-08
Canadian Army, eh? :p

---

### Post by acadiansteph on 2007-05-08
Yay another canuck. Yes ,army of Canadian Ubuntu users!!!:lolflag:

---

### Post by houstonbofh on 2007-05-08
I would have said that viruses don't run in Wine, but there was an announcement a week or so ago abut a team making a windows virus work in Wine.  I have no clue why...  Still, the virus is user level, so easy to kill.

---

### Post by starcraft.man on 2007-05-08
> **acadiansteph said:**
> Yay another canuck. Yes ,army of Canadian Ubuntu users!!!:lolflag:

We will do the world a favor, and once our online army is amassed, we shall take out Gates and Microsoft in one swoop, we beat the odds at vimmy, we can take on anyone :p

> **houstonbofh said:**
> I would have said that viruses don't run in Wine, but there was an announcement a week or so ago abut a team making a windows virus work in Wine.  I have no clue why...  Still, the virus is user level, so easy to kill.

Well, what happens is that WINE (and cedega and crossover) emulate the APIs and other protocols that certain programs use. If it just so happens that Virus X is programmed to detect and attack/latch on/corrupt that same API or protocol or other windows function, it will work under WINE. So it isn't really something new, its more of an unfortunate byproduct. Of course, I would assume that less viruses affect WINE than a full install of windows. As you said though, even if it was coded to pop out of its virtual container into Ubuntu (VERY unlikely, but I think proof of concept ones have been specifically made) the fact that your just a user and not admin, would prevent most serious damage.

---

