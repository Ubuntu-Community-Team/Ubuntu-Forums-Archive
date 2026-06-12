---
title: "Problem Burning Ubuntu CD-Can't Find ISO File"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by wpwend42 on 2007-08-24
Alright, I downloaded the ubuntu-7.04-desktop-i386.iso torrent.  When completed, it gave me a zip file which I extracted, giving me a set of folders.  Where is the ISO file I need to burn?  I tried to burn the image in InfraRecorder but I can't find it!  

I installed Ubuntu once before and don't remember having this problem.  If someone could point out what I am doing wrong I would greatly appreciate it.

---

### Post by carloslosgrande on 2007-08-24
[FONT="Comic Sans MS"]Hi. Don't extract it - burn the download direct to disc as an iso file.[/FONT]

---

### Post by philinux on 2007-08-24
You should have clicked the link below to downloaded.

[http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso) 
there is no torrent involved it just downloads one file which you then burn as an image.

---

### Post by wpwend42 on 2007-08-24
Ok the first reply worked!  Thanks.  Now I am in the live CD, but my wireless connection won't work.  I can't remember if my other computer's internet worked on the live cd, is that unusual?  The laptop I am installing on is pretty new (little over a year).  I just want to make sure the internet works before I leave Windows behind for good.

---

### Post by philinux on 2007-08-24
From what I've read on here wireless is a minefield. do a search on the forums.

The key seems to be to identify you wireless card and see if its supported.

---

### Post by mlentink on 2007-08-24
> **philinux said:**
> From what I've read on here wireless is a minefield.
I would rather say it can be if your card is not supported out of the box. It should be fairly easy to find out the make and model of your wireless card, and with that info search these forums, there's loads of info on getting your wireless installed and running. 
Posting the make and model of your laptop could help us helping you finding out the specs of your WifI-CARD

---

### Post by philinux on 2007-08-24
If you've seen this page before ignore

[http://www.linux.com/feature/118497](http://www.linux.com/feature/118497)

I you scroll down there is a good piece on wireless
Good luck with your install

---

### Post by wpwend42 on 2007-08-24
According to the live CD terminal, I believe my wireless is a Broadcom BCM 4318 [AirForce One 54g} 802.11g wireless lan controller.

---

### Post by wpwend42 on 2007-08-24
I see this in another forum:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

But will it work on the live CD?

---

### Post by mlentink on 2007-08-24
There's actually a lot of info about that card in the forums already. Let us know if you get stuck.
Sorry not to be of any help right now, but I'd have to check those threads as well. I do remember it is not supported out of the box, so you'll probably have to hunt for Linux drivers or use ndiswrapper (which alllows you to use the windows-driver for it)

---

### Post by SlowRedFox on 2007-08-24
I've found that Broadcom cards work best with ndiswrapper, a program that lets you load the windows driver for the card, rather than the open source driver, which was extremely slow and had difficulty connecting. Instructions on installing broadcom 43xx cards with ndiswrapper are [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") for to-the-point instructions. After the driver is installed, you can connect to your network with the networkmanager applet.

---

### Post by wpwend42 on 2007-08-24
I am going to try what is mentioned in that thread on the live cd.  

I just don't want to install ubuntu until I know the wireless works.  My other computer running Ubuntu works great, and that one is probably 4 years older than my laptop!

---

### Post by wpwend42 on 2007-08-24
Wait, how is any of this going to work if I can't access the internet?

---

### Post by wpwend42 on 2007-08-24
Alright I tried the above links and none of them are working for me.  I also tried this and it doesn't work either

[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

This is extremely disappointing.  I despise Windows and was really looking forward to not having to be infested by spyware anymore.

---

### Post by SlowRedFox on 2007-08-24
Define "doesn't work"? Did you use network manager to connect? Did you compile ndiswrapper from source as that thread suggested?

---

### Post by wpwend42 on 2007-08-24
Network manager doesn't show a wireless connection any more.  While in the live CD, in system-administration-network after doing the above thread i linked, I only see "wired" and "modem" connections.  In the top right corner, where it usually says "enable networking" and "enable wireless" it only says the former now.  

I followed the instructions in the terminal for compiling ndiswrapper.

---

### Post by wpwend42 on 2007-08-24
I also tried to install the wifi-radar package as the terminal said, but when I searched nothing came up on the live CD.

---

### Post by wpwend42 on 2007-08-24
Would it be possible to switch out my wireless card? Or use a wireless PC card or adaptor instead? My desktop computer has a wireless adaptor (d link I believe) and it connects to ubuntu great (i am posting via it right now)....but i don't think i have the ports for that....do they make USB versions maybe?

---

### Post by wpwend42 on 2007-08-24
I'm just gonna go back to Windows, thanks for your help everyone.

---

