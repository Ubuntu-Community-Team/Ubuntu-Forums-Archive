---
title: "Idiot here, help with installing/wireless network"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by monsieur fatso on 2006-10-05
Hey guys, I've tried finding help on this, because I know that "DURR INTERNETS HELP ME PLEEZ" posts are kind of annoying. Sorry if I'm totally missing something, and for my lack of computer literacy.

I decided I want to try out Ubuntu because I'm not a big fan of Windows and it being so glitchy, and I don't feel like forking over half a years worth of work to get an ibook.

Anyways, I booted up from the cd, just to make sure I like it, before I commit to pretty much deleting everything from my computer and what not. Maybe it's just something that you can't do when booting from the cd, but I couldn't get any webpages to load. If it's just because I was running the OS from the disk, great, problem solved. If not, I'll try and provide as much info as I can. 

First of all, I get my internet through a wireless connection, that I'm not really sure where it comes from. It's always there though. I tried looking up my wireless card on the list under the help section, but didn't see it. In the device manager (I'm running xp right now), under network adapters, it says my wireless card is Dell Wireless 1350 WLAN Mini-PCI Card.

If there's any other info you need, just ask. Any suggestions you guys have would really be appreciated. Thanks.

---

### Post by halitech on 2006-10-05
I don't have a wireless card myself but from what I've read, you may need to install, get ndiswrapper and install your NIC drivers from the windows driver to get wireless to work. Someone with wireless and more info will probably be along shortly

---

### Post by Fully216 on 2006-10-05
You should be able to get your wireless working by installing the ndiswrapper package.  It is well documented that this wireless chipset can work on multiple operating systems, Fedora and Ubuntu included.  

To find out if you card is supported, I usually first do a search for the chipset found in your card.  It happens to be a Broadcom chipset (43xx).  This makes me hopeful that it will work because I use the 4306 chipset.

To check for support I usually check the aircrack compatibility and TuxMobil, both found here.  

[http://www.aircrack-ng.org/doku.php?id=compatibility&DokuWiki=71f4f31837352db849ccff519aef84cd](http://www.aircrack-ng.org/doku.php?id=compatibility&DokuWiki=71f4f31837352db849ccff519aef84cd)
[http://tuxmobil.org/minipci_linux.html](http://tuxmobil.org/minipci_linux.html)

You can see that some have had luck with your card, others not so much.

Most importantly, I check the list found on the official ndiswrapper site for confirmation.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

This means that it can be done, although I know that many people have difficulties depending on your level of computer know how.  Since your card is the AirForce One 54g card, I specially remember reading through a couple of howto's because my card is so similar.  There are a few of them listed here.

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
[http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card](http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card)

I do not recommend using the fwcutter package.  I tried it without realizing it crashes amd64 systems that have more than 1 GB of RAM, as I conveniently do.

Just search around the forum and you can find a lot more help with regard to you wireless card.  I think with a smidge of help you will be able to get it working without to much hassel.  Finding the right 'how to' will be key and being willing to play around with it for a day or so until it is working is all you need.

---

### Post by monsieur fatso on 2006-10-06
Thanks a ton. My connection I have here is spotty at best, so I'll have to take my computer into work with me this Sunday to try and get this to work. I'll let you know how this works.

---

