---
title: "I don't think I'm ready for Ubuntu yet"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Hysterix on 2007-01-31
Hi all,
First some background... I've been with Windows since 3.11 and know it pretty well. I'd say to a fairly advanced level.

I've wanted to come away from Windows for a LONG time as I'm fed up with the crashes, the security threats, etc. and certainly don't want to fork out for Vista when we have 5 pc's in the house!

So yesterday I downloaded Edgy and installed it on my laptop as a "testing ground". The live version didn't run. After some googling I reburned the disk at a much slower speed and hey presto - it worked!

Had a "play", noticed my wireless PCMCIA card didn't have any lights on (a Belkin F5D7010 using the Broadcom chipset... I checked in Windows and copied the driver to a flash drive ;) ). No problem, I thought I'd give it a go anyway and went ahead and installed. 

Install went without a hitch. Perfect. No problems at all.

After that was complete, logged in and noticed still no signs of life from the PCMCIA card. Tried googling again and was swamped with info! Try this, try that, install this, etc... The problem is, it seems to ALL assume you have some knowledge of how to do all of this! 

Also, our network is secured using WPA-PSK (TKIP). I saw no easy way of even connecting to the network should the card have worked. However, I did notice that plugging my wired connection works - but as the cable modem & router are in a different part of the house to all the PC's, that isn't really going to be a long-term option. 

So that's problem one...

I thought I'd give it a go on my MAIN PC... (this one) as it's the newest system in the house. This time, I can't even get to install it as it uses SATA hard drives and for some reason the repartitioning screen simply does nothing after I click the "Forward" button on screen 5 (i.e. after telling it to resize the drive 25% ). This one I REALLY don't know where to start as I don't know much about SATA at all. All I know is I have two 160Gb drives, 100Gb free on the C: drive (where I want to install Ubuntu), and there is no RAID in place (as far as I know. The 2nd drive acts like a normal 2nd drive. Not a mirror of the 1st or anything.

I would LOVE to get Ubundu set up and working on all 5 pc's as I really like the philosphy, and the availability of software (even up to getting my beloved World of Warcraft running!) but I don't know if it's going to be possible given that I am so completely in the dark!

If anyone could help and talk me through what to try, step by step, treating me like an idiot(!), I'd appreciate it... but I fear that I'm asking a lot!

---

### Post by K.Mandla on 2007-01-31
I can speak for the F5D7010 -- I used to have one, and also ran into too many problems getting it set up, and so I took it back to the box store and picked up one that was a little more linux-friendly. 

I realize that's a rather drastic option, but it is one way of casting a vote in favor of companies that open-source their drivers, or at least make their components more compatible with non-MS operating systems.

By the way, welcome!

---

### Post by pissedoffdude on 2007-01-31
> **Hysterix said:**
> Hi all,
First some background... I've been with Windows since 3.11 and know it pretty well. I'd say to a fairly advanced level.

I've wanted to come away from Windows for a LONG time as I'm fed up with the crashes, the security threats, etc. and certainly don't want to fork out for Vista when we have 5 pc's in the house!

So yesterday I downloaded Edgy and installed it on my laptop as a "testing ground". The live version didn't run. After some googling I reburned the disk at a much slower speed and hey presto - it worked!

Had a "play", noticed my wireless PCMCIA card didn't have any lights on (a Belkin F5D7010 using the Broadcom chipset... I checked in Windows and copied the driver to a flash drive ;) ). No problem, I thought I'd give it a go anyway and went ahead and installed. 

Install went without a hitch. Perfect. No problems at all.

After that was complete, logged in and noticed still no signs of life from the PCMCIA card. Tried googling again and was swamped with info! Try this, try that, install this, etc... The problem is, it seems to ALL assume you have some knowledge of how to do all of this! 

Also, our network is secured using WPA-PSK (TKIP). I saw no easy way of even connecting to the network should the card have worked. However, I did notice that plugging my wired connection works - but as the cable modem & router are in a different part of the house to all the PC's, that isn't really going to be a long-term option. 

So that's problem one...

I thought I'd give it a go on my MAIN PC... (this one) as it's the newest system in the house. This time, I can't even get to install it as it uses SATA hard drives and for some reason the repartitioning screen simply does nothing after I click the "Forward" button on screen 5 (i.e. after telling it to resize the drive 25% ). This one I REALLY don't know where to start as I don't know much about SATA at all. All I know is I have two 160Gb drives, 100Gb free on the C: drive (where I want to install Ubuntu), and there is no RAID in place (as far as I know. The 2nd drive acts like a normal 2nd drive. Not a mirror of the 1st or anything.

I would LOVE to get Ubundu set up and working on all 5 pc's as I really like the philosphy, and the availability of software (even up to getting my beloved World of Warcraft running!) but I don't know if it's going to be possible given that I am so completely in the dark!

If anyone could help and talk me through what to try, step by step, treating me like an idiot(!), I'd appreciate it... but I fear that I'm asking a lot!
Try typing this command ```
 lspci | grep Broadcom\ Corporation
```
if your output is similar to ```
spci | grep Broadcom\ Corporation
0000:02:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
``` then ur in luck and could follow this howto [http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom") If not then take a look at this howto [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/44780-getting-wireless-lan-card-work-linux.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/44780-getting-wireless-lan-card-work-linux.html")  You should be able to get WoW running perfectly under wine

---

### Post by punkybouy on 2007-01-31
I bought a Belkin card at Staples.  Wireless G notebook card.  I had to search for the right inf file to use with ndiswrapper and I found it here on the forum somewhrere but I got it loaded and the card works great and that was with Dapper.

---

### Post by saadakhtar on 2007-01-31
please post the specs for your computers. and the model # for the wlan card. I am sure we can find a way to get it to work.
I too started using ubuntu and experienced the strangest problems. had wlan card not working. graphics card not working and then "my favourite" the screen resolution issue. i had to read pages and pages of stuff before i could get it to work but since then i have a good hands on the issue.

---

### Post by podunk on 2007-01-31
Welcome! :)

The thing about Edgy (6.10) is when it works it works great, but if it doesn't work great right off the bat and you're new you have a long row to hoe. If you continue to have trouble setting edgy up on your main computer you might want to fall back to Dapper while you learn a bit more about Linux

As far as setting up your main PC- back it up first.

I cheat. I use Windows <blush!> to partition and re-size my drives then install. I am familiar with the interface, it's easy and I'm not the sharpest tack in the pack anyway. Windows will pretty well protect itself from itself so the danger of data loss is reduced.

I make 3 empty partitions. One 2 gig for swap, one 10 gig for root (aka / ) and the rest for /home

It's pretty easy for me to set everything up when I have some nice big empty targets to aim at.

---

### Post by wpshooter on 2007-01-31
Hysterix:

Hang in there.  I have probably been using computers of some sort for the past almost 30 years now.  And let me says that this (Ubunt/Linux) is quite a challenge especially when you have no FORMAL IT training.

First remember that this is NOT M/S windows or at least not yet.  There is a lot of code that is yet to be written before this O/S is anywhere near as user friendly as M/S.  And by that, I mean the development of GUI tools to perform a lot of functions and configuration work that must be performed now by having knowledge of the terminal commands and/or by knowing where and what to change in configuration files to fix problems.

You will find that there is a vast number of die hard Linux users that will cry bloody murder if you purpose moving away from these NON-GUI tools.  However, I am fairly confident that in the next few years that if Canonical wants Ubuntu to become a widely used O/S that these GUI tools will slowly be made available.  So until then, you, I and the majority of other novice Linux users are going to have to rely on this and other forums to get the knowledge we need to setup and maintain these systems.  But don't dispair, I have switched (I have NO M/S on my machines) all 4 of my machines from M/S to Ubuntu and they can do a lot of what I need and like to do with a computer.  One thing in my favor is that I do NOT want to have anything to do with WIRELESS.  Give me a good old hard wired network any day.  That is what mine is.  Using a simple Netgear 8 port hub (not router) and that tied into my Verizon DSL modem/router.

To make a long story short there is surely a LOT more about the O/S that I don't know than I do, but with the use of this forum I think I can come up with most of the answers I really need to get things going.

P.S. - My suggestion would be that you stick with Dapper for NOW instead of Edgy.  Then might want to consider changing to Feisty when that becomes stable.  

I am sorry I can not help you with the wireless, but there are many forum users that can.  If you have other specific questions post them one at a time and we will surely try to get you some answers.

Good luck.

---

### Post by Tux Aubrey on 2007-01-31
Welcome

I had the same two problems when I first started (plus a few others).  The posts above are a good start to getting WiFi working. ndiswrapper worked for me, but I have Netgear and D-Link PCMCIA WiFi cards.

There are also posts about SATA on these forums.  In my case (drives "timing out" causing excessively long boot times) none of them helped but when the Linux kernel was upgraded recently, SATA suddenly booted fine.

Use the How-Tos on this site and on others - (insert big plug for [http://psychocats.net/ubuntu/index.php)](http://psychocats.net/ubuntu/index.php)).  

Believe me when I say it is worth a little difficulty at the beginning to get  Ubuntu working.  If you find it all too much do try another Linux distro - Suse, Mandriva, Fedora - they all have their pluses and minuses.

---

### Post by Hysterix on 2007-01-31
Hi again,

Thank you for your replies - especially wpshooter. You've encouraged me not to throw in the towel just yet! 

I have several wireless cards including the centrino one built in to the laptop. In fact I think I'll start there... get the laptop set up and running on Dapperm use that to learn and then move on to the other pc's. Otherwise I'm biting off way more than I can chew!

So tomorrow I'll download Dapper and install that. I guess that during the installation there's an easy way to delete the current Edgy installation and use that partition for Dapper? (In fact I'm sure there is!)

I agree - any form of Linux that I've heard about is still a long way off the "user friendliness" of Windows - but it IS coming, and in the mean time, it's a LOT more stable - and the community is infinately more friendly!

Thanks again... I'll shout again tomorrow when I get stuck! :)

Edit: Thanks Tux Aubrey - we crossed posts :) Yes, I'm definately sticking with it. The effort will pay back many times over in the long run. And it's fun to learn. If it wasn't, then why bother? :)

---

### Post by Hysterix on 2007-01-31
> **punkybouy said:**
> I bought a Belkin card at Staples.  Wireless G notebook card.  I had to search for the right inf file to use with ndiswrapper and I found it here on the forum somewhrere but I got it loaded and the card works great and that was with Dapper.

Mine came from Staples too! Maybe (hopefully) it's the same one!

I need to learn how to use ndiswrapper (actually, before that I need to practice installing ANYTHING!!). I'm sure that I can crack this - even if it tales a little while!

---

### Post by Hysterix on 2007-01-31
> **pissedoffdude said:**
> If not then take a look at this howto [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/44780-getting-wireless-lan-card-work-linux.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/44780-getting-wireless-lan-card-work-linux.html") 

That's a fantastic link - thank you so much!! Everything step by step. Brilliant! Will try that tomorrow.

>  You should be able to get WoW running perfectly under wine

Even with Burning Crusade? I REALLY hope so!! If that's the case, it's bye-bye Windows forever!

---

### Post by spasticteapot on 2007-01-31
I can say the same. Linux has a steep learning curve.

My advice?

Step 1: Buy a thinkpad. An older 600-series should be fine, especially if you upgrade the CPU. Have at least 256mb of RAM.
Step 2: Install Xubuntu - faster and easier to use! (The latter is personal opinion; the former is verified.)
Step 3: Enjoy many years of Linux excellence!

Seriously, I'm a laptop freak - I've owned a Dell, a Gateway, a Hp/Compaq Evo, and an Apple. My Thinkpad X40 outclasses them all.

---

### Post by moshuptrail on 2007-01-31
Hey wait a sec.  Before you do anything drastic with that wireless card, I'm using the F5D7010 with Dapper and I swear it works BETTER under Linux than it did under Windows.  The install recognized it and set it up fine.  All I had to do was enter the WEP key and I was up and running.  (I did have to enter it in Hex, so I copied it from a flash drive)

So out of curiosity I just now did a modprobe -l | grep ndis (check installed drivers for ndiswrapper)
```
/lib/modules/2.6.15-27-k7/kernel/drivers/usb/net/rndis_host.ko
/lib/modules/2.6.15-27-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

```

So maybe the installer used ndiswrapper.

The output of lspci | grep Net:
```
RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
```

Maybe you can use this info.

---

### Post by Hysterix on 2007-02-01
> **moshuptrail said:**
> Hey wait a sec.  Before you do anything drastic with that wireless card, I'm using the F5D7010 with Dapper and I swear it works BETTER under Linux than it did under Windows.  The install recognized it and set it up fine.  All I had to do was enter the WEP key and I was up and running.  (I did have to enter it in Hex, so I copied it from a flash drive)

So out of curiosity I just now did a modprobe -l | grep ndis (check installed drivers for ndiswrapper)
```
/lib/modules/2.6.15-27-k7/kernel/drivers/usb/net/rndis_host.ko
/lib/modules/2.6.15-27-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

```

So maybe the installer used ndiswrapper.

The output of lspci | grep Net:
```
RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
```

Maybe you can use this info.


Lol that was WAY over my head :)

Where did you enter the WEP key? I'm using WPA-PSK and TKIP. In Windows I enter the key in plain text into the Belkin "Wireless Monitor". Hopefully it'll be nice and easy in Ubuntu. I'm currently burning the Dapper CD and will be installing it soon... I have my fingers (and toes and eyes!) crossed!

---

### Post by Evil@heart on 2007-02-01
I feel your pain friend.  I have a similar situation, I've been using Winblows since 3.11 and after having beta tested Vista for a few months,have made the switch.  Ubuntu is frustrating the crap out of me but every challenge has brought a greater reward.  1 month in and I have no idea how to do  a lot of the common knowledge stuff and I still like Linux better than the alternative.

---

### Post by FaceorKneecaps on 2007-02-01
I feel the pain too... :D 

I have tried to convert since Win 3.11 but havent done so before 1 month ago, and it's running pretty great. If you run dual boot with xp there is no reason to look back even though the learning curve is steep, because ubuntu has all the quality programs I used in xp. It look alright out of the box and even if I dont understand it all I can still download (azureus/nicotin), browse the web with firefox, listen to music with amarok, watch movies/series with vlc and write projects with Openoffice. So I have everything I need to relax and read up on the things I dont understand. I paniced the first week not knowing how to do everything like in xp, but took a deep breath and came to terms with the learning curve. If I have internet and music I have all the time in the world to learn how this os works and all its possibilities...  Thats what genious about ubuntu, It gives you everything you need to learn more.   :D

---

### Post by Hysterix on 2007-02-01
WOOHOO!!! (excuse me - but I'm excited!)

Got the built-in Centrino wireless working and installed Network Manager, so that I could use the WPA key (plain text - no hex!) - and it's working beautifully!! YAYAYAY

Also downloaded and installed Skype and that's running perfectly too!! 
nd 
To be honest, I don't have a clue how I did these (I know WHAT I did - but not why or how), but I am over the moon that it works!

Also, I can browse the other PC's on the Windows network (and it honestly is faster and easier than it was in XP)...

Next off, getting my MP3's to work! Installed amaroK but as I'm under Gnome I dont know that it will work properly... (something else for the TODO list - add KDE and learn how to switch between the two). AmaroK doesn't want tp play my MP3s currently and neither does the default player (says I need codecs) - but now it's going to be a downhill race - Wireless was the deal breaker and now that THAT works, Ubuntu is here to stay!!!

Now then... how do I print on my printer that's on one of the Windows PC's? :)

---

### Post by hyper_ch on 2007-02-01
:)
Ubuntu did recognize all my hardware (except for the BT headset) immediatly, so I never had to go through the wifi pain :)

Regarding MP3s, there's the perfect guide for you:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Basically open up the terminal and enter the follwing code:

```

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

```

that should install (almost) all codecs you'll probably ever need

---

### Post by Hysterix on 2007-02-01
Thanks so much :)

Had to add the Universe and Multiverse repositories first, but then copied your code (I was already reading that exact same How-To :) ) and now I'm listening to my music as I type this!

You know, I've found one major difference to Ubuntu over Windows... getting things working in Windows has never been so rewarding!

Next stop... printing 

Followed by... getting DVDs working

Later... the scary one... getting WoW to work! lol

---

### Post by igknighted on 2007-02-01
> **K.Mandla said:**
> I can speak for the F5D7010 -- I used to have one, and also ran into too many problems getting it set up, and so I took it back to the box store and picked up one that was a little more linux-friendly. 

I realize that's a rather drastic option, but it is one way of casting a vote in favor of companies that open-source their drivers, or at least make their components more compatible with non-MS operating systems.

By the way, welcome!

I agree completely with your moral stance on the issue, but I don't think the card is that hard to get working... I used NDISwrapper with the drivers provided on the CD and it worked like a charm.

---

### Post by jvc26 on 2007-02-01
Excellent good to see another new user. These links may prove useful for future reference/browsing:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) or dapper: [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
To name a few, enjoy :)
Il

---

### Post by skirkpatrick on 2007-02-01
I've got WoW working on 3 different Edgy computers.  I have not yet bought BC as I've only been playing for a month.  Here's a couple of hints:

1) To make some of these things REAL easy, go to [www.getautomatix.com](www.getautomatix.com) and install Automatix.  You can select audio/video codecs, Flash 9, the latest Wine, etc. and install them with just a few clicks.

2) You can follow this wiki howto for getting WoW working: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

However, I found out that it can be even easier.  I'm using Edgy and used Automatix to install the latest version of Wine.  You do need to copy all your CD's over to a temporary directory on your hard drive to install (and it installs faster also).  One thing you don't need to do is configure Wine to us the OSS sound system, it works just fine with ALSA.

3) If you have to replace a wireless card that you are having problems with, it's still cheaper than installing Vista on 5 computers :)

---

### Post by wpshooter on 2007-02-01
[QUOTE=

Now then... how do I print on my printer that's on one of the Windows PC's? :)[/QUOTE]

Hysterix:

I hope you have better luck on this one than I have.  I have never been able to get printer sharing to work on my Ubuntu network.  I think it is possible but the hoops that you currently have to jump thru to get it to work is not worth it.  I am going to just wait until hopefully they decide to do some work on making this a fairly simple process.  So until then, when I want to print something, I will just have to run upstairs.  Good exercise, I suppose.

---

### Post by Hysterix on 2007-02-01
> **wpshooter said:**
> Hysterix:

I hope you have better luck on this one than I have.  I have never been able to get printer sharing to work on my Ubuntu network.  I think it is possible but the hoops that you currently have to jump thru to get it to work is not worth it.  I am going to just wait until hopefully they decide to do some work on making this a fairly simple process.  So until then, when I want to print something, I will just have to run upstairs.  Good exercise, I suppose.

Um... I almost feel bad now... I just went to Administration > Printing, clicked New Printer, browsed to the printer on the Windows network, told it which driver to use (Epson RX500), and printed a test page. All worked fine first time!

Your advice to use 6.06 was invaluable though. Although it looks nicer here and there, I don't think 6.10 is ready for newbies like me as yet!

---

### Post by punkybouy on 2007-02-12
You could try Kubuntu.  The K desktop may be more appealing and Windows like and a tad easier to use

---

### Post by punkybouy on 2007-02-13
Get a print server.  I think they run around $50.  It gets its own IP address and everyone on your network can use it.

---

### Post by AndyCooll on 2007-02-13
> **punkybouy said:**
> I bought a Belkin card at Staples.  Wireless G notebook card.  I had to search for the right inf file to use with ndiswrapper and I found it here on the forum somewhrere but I got it loaded and the card works great and that was with Dapper.

I know the OP has resolved this issue, however I just want to post a comment about these PCMCIA cards (Belkin F5D7010 using the Broadcom chipset) in case anyone does a search later. 

You don't need ndiswrapper to get these working. There are actually different versions of the F5D7010 and they use different chipsets. I'm using Edgy and have both working. The earlier versions should work out of the box. However the newer cards use the RT61 chipset and require a bit of configuring. There's a good thread here that tells you how: [HOWTO: RT61 on Egdy Eft with WPA]("http://www.ubuntuforums.org/showthread.php?t=296822") 

:cool:

---

