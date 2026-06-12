---
title: "Big(Imo) laptop-Wireless issue."
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by TJF on 2008-02-05
Well, my dad wanted me to put ubuntu on his laptop because he basically uses it for simple things, and doesn't want the windows B-S slowing him down. I put it on, and it installed in about 15-30 minutes and seemed to work just fine, until the wireless Internet stopped working. I tried and tried to get it to work, but nothing worked.. finally, my dad said just to install windows again but we have none of the drivers installations, so i think it would just be easier to do this. Anyone know what to do to get it to work? I'll try to post what it actually is in just a bit..

EDIT:
It's a dell inspiron 1150, but I'm not sure what the actual hardware is.
EDIT2:
I found a list of it's drivers ( [http://driverscollection.com/?H=Inspiron%201150&By=Dell](http://driverscollection.com/?H=Inspiron%201150&By=Dell) ) , so I'm going to download them and install windows unless there is something someone here can do. He and I would much prefer if he had Ubuntu installed.

Oh yea, I think I remember reading something about using windows drivers to get all of the hardware working properly(?).

---

### Post by JoshuaRL on 2008-02-05
You might look on the Dell site for the specs for that laptop.  That way we can see what kind of fix it will need.

---

### Post by spiderbatdad on 2008-02-05
so the wireless just temporarily stopped working, but was working before? That is not unusual...wirelss broadband has a tendency to do that sometimes. It happens here occasionally...for an hour no computer will connect...not mac w/OSX, not windows, not my linux box. Then without warning...it's back up. I wouldn't blame Ubuntu. You might try enabling roaming mode in your wireless configuration. 

Just because you see a lot of wireless issue here, doesn't mean it is a guaranteed problem with Ubuntu. There are millions of users using wireless happily.

---

### Post by TJF on 2008-02-05
Yes, but it worked when I had windows installed(on windows and the ubuntu live cd). Then I allowed ubuntu to over-write the windows partition, and since then I can't connect to it. I think it may be a driver issue, atm, and I need to find a way of installing the drivers. Help?

Oh, and I didn't realize there were more posts(>_>) and updated the above post the best I could with info on the laptop.

---

### Post by spiderbatdad on 2008-02-05
could you port the output of ```
sudo lshw -C net
```

---

### Post by oedha on 2008-02-05
first will be what is your wireless......do like spiderdad said
after that....maybe yours can be run instantly or use madwifi or ndiswrapper

---

### Post by TJF on 2008-02-05
Did I mention I'm new to this? (..) Sorry, but I do know about basic commands in the terminal. Just not what they do, etc.

---

### Post by spiderbatdad on 2008-02-05
ok sorry...open a terminal...Applications>>Accessories>>Terminal...then copy the command exactly...including spaces and case. or copy and paste from here.```
sudo lshw -C net
``` input password due to sudo command.

---

### Post by spiderbatdad on 2008-02-05
BTW  though you were using the live cd...i believe it did load the linux modules...so you were using wireless on linux.

---

### Post by TJF on 2008-02-05
Um. Mk.

Anyways, I just realized that by trying to reinstall windows it over-wrote(is that the correct phrase?) what I had set up for Ubuntu, so It's reinstalling.. roughly 60% at the moment.

Oh, and I don't have it connected to the internet at all at the moment, I'll write it down and go down to it(It's in the basement, I'm up stairs). If it starts spitting out important information I'll bring it up and connect it through the Ethernet port..

---

### Post by spiderbatdad on 2008-02-05
that command asks for a list of hardware for networking.

---

### Post by TJF on 2008-02-05
All-righty then. Here go:
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:11:43:61:53:95
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=32 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 03
       serial: 00:0b:7d:0e:6e:19
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

---

### Post by spiderbatdad on 2008-02-05
alrighty...many folks use this wireless card.  Here is a guide:[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)  download the i386.deb. Follow the guide. Good luck. Many folks use this card. It may take a little extra work, but you can get it done.

---

### Post by TJF on 2008-02-05
[http://www.vulomedia.com/images/55958Screenshot.png](http://www.vulomedia.com/images/55958Screenshot.png)

And the description of that (from the mouse hover) was that it was the firmware needed to use my wireless card.. how can I enable that?

PS:
My dad leaves tomorrow, so I need this done before 3:00 pm GMT -7:00 mountain time.
EDIT: I have no idea why all of the windows in that picture are transparent...
EDIT2: Oh, I see, the window was still *slightly* there.. so It's just that window. None the less.. Help!?

XD
I just realized that you posted just before I did.. >_<

---

### Post by spiderbatdad on 2008-02-05
should be able to go System>>Administration>>Restricted Drivers Manager. If you did not have internet at the time of your installation...maybe your sources are not turned on. If you have nothing there to enable, please copy and paste back the result of ```
cat /etc/apt/sources.list
```

---

### Post by jordanmthomas on 2008-02-05
You need to enable the universe repository.  You can do this in System --> administration --> package manager
The option's there somewhere (not an Ubuntu user so I can't just look)

OR, you could get the deb package here, you should already have the dependencies installed:
[http://mirrors.kernel.org/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb)

---

### Post by spiderbatdad on 2008-02-05
```
gksu gedit /etc/apt/sources.list
``` make it look like mine, by removing the #'s that you see where mine are removed. Then save and exit. Then run```
sudo apt-get update
```



```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by spiderbatdad on 2008-02-06
> **jordanmthomas said:**
> You need to enable the universe repository.  You can do this in System --> administration --> package manager
The option's there somewhere (not an Ubuntu user so I can't just look)

OR, you could get the deb package here, you should already have the dependencies installed:
[http://mirrors.kernel.org/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb)

enabled by default in gutsy...he must have installed without an internet connection, so his sources are commented out.

---

### Post by TJF on 2008-02-06
THANK YOU SO MUCH!!

This post is this laptops official first wireless post! 

YOU GUYS ROCK!!! Especially you, Spiderbatdad! If you weren't able to do this, my father would have to take my mothers laptop, and she would have to commandeer the computer that I use, etc.. etc..

---

### Post by spiderbatdad on 2008-02-06
:guitar::guitar:

---

