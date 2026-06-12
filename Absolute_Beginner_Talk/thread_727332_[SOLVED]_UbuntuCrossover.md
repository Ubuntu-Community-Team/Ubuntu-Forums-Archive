---
title: "[SOLVED] Ubuntu/Crossover"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Louie928 on 2008-03-17
Hi All,
First post.
I'm new to Ubuntu although been with Windows since v 2.0. Windows Vista made me seriously explore other alternatives so here I am. I successfully installed Ubuntu 7.10 in dual boot with XP on my Toshiba Satellite laptop. Everything works. Wireless connection to my router and internet was near automatic, and only a little more fussing to get connected to my home network and other (Windows) machines. The apps included with Ubuntu and supported 3rd party programs will fill most of my needs.

Next step to eventually moving to Ubuntu as much as possible was to explore ways to run some Windows programs from Ubuntu. One choice seems to be Code Weavers Crossover. Most of my non-Linux programs wouild be in the unsupported group such as TurboCAD v14, AutoCAD, Solidworks, various electronics design, and engine simulation. I thought I'd try it anyway since there was some hope that unsupported applications may work. None of my Win programs were on the supported list so it could be a longshot. I downloaded the trial Crossover and installed that with no problems. I attempted to install TurboCAD and got a message that it needed IE5 or later. I used Crossover to install IE6. No problem there. IE worked ok. I tried again to install TurboCAD and got the same message that it needed IE5. Next, I attempted to install a graphics editor program, PhotoPlus x2. That installation stalled with the message that it needed IE5 or later. I tried to install these programs in "bottles" that were Win2000, or WinXP with the same result. I tried installing IE6 into the same bottles, but no difference. Seems like something is not passing the message that IE6 is installed, but what, and how to fix?

You may wonder why I'm bothering you with this problem since it is probably a Codeweaver problem. Their FAQs don't address this, and their email support isn't available if you have not yet bought their product. 

Any Ideas? If Crossover won't do it, maybe native Wine, maybe a VM, or fall back to dual boot.

Thanks.

---

### Post by billgoldberg on 2008-03-17
Why don't run native linux programs that do the same?

[Autocad]("http://linuxappfinder.com/alternatives?search_text=autocad")


[Solidworks]("http://linuxappfinder.com/alternatives?search_text=solidworks")

---

### Post by wolfen69 on 2008-03-17
try virtualbox [http://www.virtualbox.org/](http://www.virtualbox.org/) and install windows on it. it works great.

---

### Post by Louie928 on 2008-03-19
Thanks very much for the useful tips. I checked out some of the Linux based drawing programs. Since I already own the Win versions of what I use, I'll stick with what I have until I need to change those. Qcad that is available from the usual Ubuntu repositories is a pretty good 2D drawing app. I also downloaded and installed VirtualBox. That is an amazing utility.Very clear instructions and well thought out approach.  XP installed and runs just as if it was a physical machine. Boot time from within Ubuntu was about 45 seconds on my P4 3 gHz Toshiba laptop. Internet connection through the wireless link to my router was completely automatic and connecting to my home network also was easy. I installed a couple Windows programs and they went in fine. With VirtualBox, I see no real need for a dual boot setup unless you wanted to keep your Win stuff completely separate.

---

