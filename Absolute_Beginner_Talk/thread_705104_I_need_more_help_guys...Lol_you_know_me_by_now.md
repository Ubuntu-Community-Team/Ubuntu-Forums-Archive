---
title: "I need more help guys...Lol you know me by now"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Shadonova on 2008-02-23
Alright a few things....

As you all know, ive actually got Ubuntu 7.04 to boot a few times...


Few problems though...

-My wireless adapter wont connect...Ive tried using it without a wep key, never recognizes it. Then when i put my wep key on...Everytime i try to connect to it...it tells me I need to put in the wep key. But then when I do, it never finds it...

-Sometimes freezes at the bootup screen.

-ALWAYS freezes on shutdown...Itll start the music it gives when it shuts down, then starts skipping one beat and freezes...


Those are my only problems right now...can you help me?

And im a total noob, I know NO lingo about some of the advice im giving...Please lamanes terms..

---

### Post by Yoke &amp; Chung on 2008-02-23
Hi,

Maybe put down your card model and chipset it is using, and someone might be able to help.

Your wireless card symptoms look very much like the problem I used to have on my wireless card. I have to use ndiswrapper to install the wireless driver and it works 100% now :-)

The following has a very comprehensive instruction to installing wireless using ndiswrapper:

[http://ubuntuportal.blogspot.com/2007/03/how-to-install-windows-wireless-drivers.html](http://ubuntuportal.blogspot.com/2007/03/how-to-install-windows-wireless-drivers.html)

Not sure on what is causing on the freezes during bootup and shutdown. Sorry, can't help you on that.

---

### Post by northern lights on 2008-02-23
Card model would be a good start.

Sounds very much like it could be Broadcom. If it is, check this [HowTo for Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty")

As far as the freezing's concerned, if anybody's supposed to have an idea, more hardware specs are needed. Give as much as you can (you're keyboard manufacturer, etc. excluded...)

---

### Post by Shadonova on 2008-02-23
Im using a laptop so how do i check things like that....



anyways....my card is Dell wireless 1390 WLAN mini=PCI card....



Idk why its labeled dell in a 1000 dollar hp laptop but w/e....


anyywas...thats my laptop wireless card...beyond that...how do i check my keyboard maker and such?

---

### Post by Shadonova on 2008-02-23
???

---

### Post by Martje_001 on 2008-02-23
For the start-up problems, look in the logs-files.

For the shutdown-problems: run this in a terminal;
```
sudo shutdown -P now
```
does it shutdown?

---

### Post by northern lights on 2008-02-23
> **Shadonova said:**
> my card is Dell wireless 1390 WLAN mini=PCI card...
That card has a Broadcom chip, this [HowTo for specifically your card]("http://ubuntuforums.org/showthread.php?t=297092") will help. That link is by the way the very first result, if you simply google "dell wireless 1390". You don't even have to put "ubuntu" in the google request, it still comes up first...



> **Shadonova said:**
> how do i check my keyboard maker and such?
Reading posts carefully is said to be helpful...
Peripherial components are exactly not what I asked for. CPU, Graphics Card, mainboard chipset (a good source for that info might just be [www.hp.com]("http://www.hp.com"))? Which Ubuntu (i386 or 64bit)?

---

