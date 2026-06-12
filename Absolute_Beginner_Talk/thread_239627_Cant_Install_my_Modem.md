---
title: "Cant Install my Modem?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by noom on 2006-08-19
Hi, 

I just installed Dapper Drake and I can't install my ADSL USB Modem its the Sagem Fast 800-840 modem, on it? ](*,) 

Does anybody know how to?

Please help, im a complete n00b.

---

### Post by noom on 2006-08-19
I just wanted to say that I quit using Ubuntu for the pure fact that I cant access the internet with it. If the ubuntu team wants any suggestions, try making the most important element of computing **easy **to access, the Internet. I tried following some tutorials that are on the forum and they dont work for some reason. 

*Does any one know if SuSe is easier to use and easier to install adsl modems and hardwares?*

---

### Post by awkward1234 on 2006-08-19
USB modems notoriously difficult to set up, better to get an ethernet modem/ router, see this link; 

[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=3092](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=3092)

not confined to Ubuntu, all Linux have this problem, basically as I understand it, most USB modems are "Winmodems" ie set up to run under Windows. 

Here's a link showing how "easy" it is to set up Linux on your modem; 

[http://www.linuxquestions.org/questions/showthread.php?t=202072](http://www.linuxquestions.org/questions/showthread.php?t=202072)

I bought a router, which was automatically found by Ubuntu.

Good luck!:-D

---

### Post by noom on 2006-08-19
I wish the best for ubuntu but i think the main milestone it'll need is to conquer the user friendlyness of it all. Possibly abolish the whole terminal concept or keep that for advanced users. I would have thought that there is a cross platform app for hardware as there is for software, on ubuntu. People talk about the sagem fast being winmodem and compatible only with windows well how come flash and dreamweaver can work on cross platform.

its 2.53am just feel like chatting aloud of crap, how ever many good ideas come out of a loud of bollocks.

:-#

---

### Post by Christopher on 2006-08-19
> **noom said:**
> I wish the best for ubuntu but i think the main milestone it'll need is to conquer the user friendlyness of it all. 
:-#

Im a newbie to linux and im doing great & love Unbuntu. Heres a few links i read before installing Ubuntu.

[http://www.ubuntuforums.org/showthread.php?t=63315](http://www.ubuntuforums.org/showthread.php?t=63315)

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

I find it very user friendly and the Ubuntu community is wonderful.

---

### Post by aces21 on 2006-08-22
I wote a howto for getting the Sagem Fast 800 USB modem to work in Dapper. You can find it [here]("http://www.ubuntuforums.org/showthread.php?t=201127"). It does make use if the command shell so if you're completely new to Linux then it might not be that straight forward, but it is written so you can just cut and paste commands from the howto into the shell. Its worth a go.

---

### Post by MaximB on 2006-08-22
to configure your ADSL modem just type in the terminal :
**sudo pppoeconf**
that's it
no big deal.

---

### Post by az on 2006-08-22
> **noom said:**
>  People talk about the sagem fast being winmodem and compatible only with windows well how come flash and dreamweaver can work on cross platform.


Well, first of all, Flash and deamweaver are proprietary.  And the latest version of flash for linux is 7.  If flash were free-libre open-source, it would likely be much more current and stable.

Hardware vendors chose to not support linux.  If they released specs or free open-source drivers for their stuff, the community would take it up and maintain it.  Their hardware would continue to work with linux without any further investment from them.

Hardware vendors and manufacturers will probably start to collaboate more and more with free-libre open-source as it takes up more and more marketshare.

---

### Post by noom on 2006-09-03
> **MAXDDARK said:**
> to configure your ADSL modem just type in the terminal :
**sudo pppoeconf**
that's it
no big deal.

what does that do, and what do i configure it too, linux doesnt read the modem. I tried Aces tut, it doesnt seem to work for mine.

Does any body actually know if Ubuntu in the near future will ever crack this situation with Sagem modem?

---

