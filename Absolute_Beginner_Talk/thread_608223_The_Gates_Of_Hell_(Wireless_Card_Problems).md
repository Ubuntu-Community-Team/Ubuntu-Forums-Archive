---
title: "The Gates Of Hell (Wireless Card Problems)"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by mouko on 2007-11-09
You clicked this 'cause you were curious about the title, didn't you?  Well, this thread is about hell; the hell that linux puts you through with wifi.  
[quote=lwconfig]eth1      IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/quote]

So my system sees the card, but is not picking up any signal.  I've looked at so many threads about my card: the dreaded BCM4318.  (Seriously, the Ubuntu team should do something about this.  I know it isn't their problem, but it is a prevalent problem nonetheless.)  So, anyone have any idea how I can get this infernal thing to work?  Hold my hand?  Have pity enough to spoon-feed a newbie through these turbulent times?

If you help me I'll give you a bottle of my mead. :guitar: (pickup only :lolflag:)

EDIT: I have no life and all weekend.  I can keep bumping this thread 'til hell freezes over.  Or until Monday comes.  Or until I get banned.  Either way...

---

### Post by sloggerkhan on 2007-11-09
I have the said card. On my comp after installing gutsy, I just clicked on the box in the restricted driver manager and it started working. I have also had it working with ndiswrapper.

---

### Post by HermanAB on 2007-11-09
Go to the ndiswrapper web site and start reading:
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

Alternatively, install Mandriva 2008 - it has a wizard for everything, including an option for ndiswrapper right in the network wizard.

---

### Post by Pumalite on 2007-11-09
Ndiswrapper is a good link to start. Check these too:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[http://ubuntuforums.org/showthread.php?t=586387](http://ubuntuforums.org/showthread.php?t=586387)
[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by mouko on 2007-11-09
> **sloggerkhan said:**
> I have the said card. On my comp after installing gutsy, I just clicked on the box in the restricted driver manager and it started working. I have also had it working with ndiswrapper.

I just did that and rebooted, still nada...  

What exactly should I be reading on the ndiswrapper site?  I've had that program installed for several days and have used it in installing the drivers.  Is there something more I need from it?

---

### Post by SunnyRabbiera on 2007-11-09
> **mouko said:**
> 

So my system sees the card, but is not picking up any signal.  I've looked at so many threads about my card: the dreaded BCM4318.  (Seriously, the Ubuntu team should do something about this.  I know it isn't their problem, but it is a prevalent problem nonetheless.) 
well then you should bloody know better then to gripe about it, I mean oy vey man

---

### Post by mouko on 2007-11-09
Sorry to come across as griping.  I actually curtsied when I posted that, so I meant it in the utmost respect.  I guess I should have learned from my experiences as a Windows user:  If something doesn't work, and you can't fix it, sit down and shut the hell up, 'cause you damn sure aren't going to get much support, aside from that of people telling you to stop griping.  esta loca...

---

### Post by Pumalite on 2007-11-09
Linux has a learning curve like any OS. We are helping you. I gave you enough to read and to learn for a week.

---

### Post by mouko on 2007-11-09
Don't worry Pumalite, I'm going through some of those pages right now.  Just figured that it might help to get some expert advice.

---

### Post by Pumalite on 2007-11-09
It's you the one that has to get buzzy.

---

### Post by mouko on 2007-11-09
Totally understand that, but I'm sure you can appreciate how draining it is to work on a problem for two weeks and not make any headway, on a problem that is so trivial on other systems.

---

