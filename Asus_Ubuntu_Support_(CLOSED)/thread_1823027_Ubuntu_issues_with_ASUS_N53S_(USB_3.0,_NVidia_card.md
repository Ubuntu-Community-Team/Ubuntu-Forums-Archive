---
title: "Ubuntu issues with ASUS N53S (USB 3.0, NVidia card)"
date: 2011-08-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by yallaen on 2011-08-11
Greetings!
First, let me say that I've just started using Ubuntu. I had Win 7 64 bit on my ASUS N53SN, which I purchased the end of May. My HDD has failed, becoming misaligned and bad boot sectors. Windows became totally unstable. I could have reloaded it, but I'm in Iraq, and forgot my back up DVD's back home in the US that I made when I first got the computer :( So, I had Ubuntu Live CD 11.04. I was able to get that running. I wiped the HDD, and loaded Ubuntu onto the HDD. I'm having occassional issues, but it's at least working for now until I get my new HDD and disks...

But my problem is concerning the USB 3.0 that's on my ASUS, as well as the onboard NVidia card. First, let's address the USB 3.0:

My USB 2.0 ports are working just fine. However, when I plug anything, including my WD My Passport USB 3.0 external HDD into the USB 3.0 port, nothing is seen. Now, I know that there was a third party vendor that provided the USB 3.0 drivers for WIndows. I've tried to use the "update drivers" in Ubuntu, and it doesnt locate/recognize the USB 3.0 slot. Any thoughts or suggestions?

Next is the nVidia GeForce GT 550M video card. This particular ASUS laptop comes with an intergrated Intel video card, and then it has the nVidia card on top of it. I noticed that when I played games in Win 7 that I could specify which graphics card to use; default was the nVidia. However, when I still had Win 7 loaded on the HDD and was running Ubuntu from the LiveCD, I could use the 3d Destiny package no problem. When I loaded it onto the HDD, it said that my PC could not support the 3d Destiny; it does not see the nVidia card. WHen I look for updated drivers, it shows that there's nVidia driver to be used, but does not give me the option to activate or enable it.

Now, I like to think I'm somewhat computer saavy. But, I've really never played with Linux, so this is a total crash-course on this OS. So please be gentle with your responses :)

---

### Post by cez801 on 2011-08-20
Hi,
I have a ASUS N53S with exactly the same issue on the NVidia card. It ran perfectly from the live CD (unity and all), but after installation on my local drive the NVidia is not working.
The Additional drivers says 'This driver is activated but not currently in use'. 

I have tried re-installing the drivers a couple of times.
The NVidia card is GT550M. 

Thanks.

---

### Post by maxpowers43 on 2011-08-24
yallaen: the additional drivers is only going to show results for hardware that requires 3rd party proprietary drivers. so it does not apply for your usb #.0 port as subsequently isn't showing anything. i would direct both of y'all to this: [https://help.ubuntu.com/community/Asus_N53](https://help.ubuntu.com/community/Asus_N53)
i just got a n53sn and installed ubuntu when i get around to checking the usb3.0 port, i'll repost if there's some special steps i have to take to get it working. as far as the video card you have to blacklist the nouveau driver. when you install the proprietary nvidia driver from the repos via additional drivers it creates a blacklist file but i had to actually add it to blacklist.conf for it to keep nouveau from loading. open a terminal>type sudo nautilus>enter password>navigate to etc/modprobe.d>double click blacklist.conf and add the following lines to the end of the file on new lines and save.>restart> and voila! 
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

ps google optimus, ubuntu and look for the bumblebee ppa. bumblebee is supposed to allow you to use both onboard video and discrete based on the application in use. i haven't got it working yet but i think i know why. i'll repost when i do.
good luck with ubuntu. it can be a little challenging at first but once you learn a little about it you'll appreciate it more and more. i've been using it in a dual boot config since 8.04 and now i only boot into windows when some foreign hardware manufacturer requires active x to flash router firmware or something stupid like that. show stopper regressions for me have all but ceased and of course i've been virus free since 8.04

---

### Post by alexy_ on 2011-08-26
I'll add about my own experience with bumblebee. 
First I started with this: **[COLOR="Blue"][https://github.com/MrMEEE/bumblebee]("https://github.com/MrMEEE/bumblebee")[/COLOR]**. I'm novice so i can't say exactly what was wrong, but after that installation i got system hangup on boot. 

After making a post on project's issue tracker i was advised to try a branch: **[COLOR="blue"][https://github.com/Bumblebee-Project/Bumblebee]("https://github.com/Bumblebee-Project/Bumblebee")[/COLOR]**, and it works for me. Also there is a little instruction in REAME how to install driver: > If you want newer drivers than the one available in the official repos, run:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 So now i have driver that working and switcher (optirun) to run application with NVIDIA-card.

---

### Post by maxpowers43 on 2011-08-27
i'm using the bumblebee ppa. it was working all along i just didn't
know i needed to run the app from the bumblebee indicator(or cli). also during setup of bumblebee you have to select a config to find out what the config is. you will have the opportunity to back out and select different config if you don't like the one you selected. then i installed bumblebee ui via synaptic and now the client has a bumblebee panel icon that he can use to initialize apps requiring MAXIMUM POWER! Oh yeah bumblebee will install the latest nvidia driver as part of it's installation. just blacklist as described previously and all your graphics issues should be solved.

---

### Post by lancest on 2011-09-07
Got this model: N53SN, NVidia GT 550M
Could someone point me (further) to the instructions that actually work for graphics switching?
 Tried a couple of times in a hurry with no success.
Boy will I be happy when it works!

---

### Post by alexy_ on 2011-09-07
one of the possible ways:
[https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee)
instructions in README (opening with link)

---

### Post by lancest on 2011-09-07
Thanks to all who gave info in this thread.
It worked on my new N53SN.
Immediate temperature drop (I was using Windows because of this)
Battery life 1-3 hours increase.

---

### Post by Oliviakrk on 2011-09-07
Could you show how you sources.list looks?
```

sudo cat /etc/apt/sources.list

```

---

### Post by lancest on 2011-09-07
# 

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

### Post by Harp32Wil on 2011-09-07
just blacklist as described previously and all your graphics issues should be solved.[img]http://www.makemoneymakemoney.net/1.jpg[/img]
[img]http://www.makemoneymakemoney.net/2.jpg[/img]
[img]http://www.makemoneymakemoney.net/3.jpg[/img]

---

### Post by rcrutzen on 2011-12-23
> **lancest said:**
> Thanks to all who gave info in this thread.
It worked on my new N53SN.
Immediate temperature drop (I was using Windows because of this)
Battery life 1-3 hours increase.

My N53SV with GeForce GT540M is generating way too much heat. I'm really curious of what what you did to cause the temperature drop, because the described steps in the readme file are not working for me. Could you please describe more clearly how you managed to drop the temperature, or give me some advise of what I did wrong?

I'm using Ubuntu 11.10 and this is what I did:
- I installed Bumblebee (
- Added myself to the bumblebee user group, then rebooted
- I installed acpi-call-tools
- edited the bumblebee.conf file
- created 'cardon' and 'cardoff' files in /etc/bumblebee
- added \_SB.PCI0.PEG0.GFX0.DOFF to the cardoff file (source: [this]("http://hybrid-graphics-linux.tuxfamily.org/index.php?title=ACPI_calls") page)
- couldn't find what to add to the cardon file, so left it empty
- after reboot, Gnome 3 didn't start, so I uninstalled bumblebee and removed cardon and cardoff.

---

### Post by devildon on 2012-03-21
Hello guys, thanks for all the useful information.
Unfortunately I still have my laptop stuck the first 2-3 times I switch it on or as I reboot. Some strange effects are shown on the screen and the laptop is blocked.
I have an Asus N53SN running with Ubuntu 11.10 64 bit and I have Bumblebee 3.0-1 installed. I also added the blacklist as you suggested before in this forum.
Could you please help me? I'm a novice with Ubuntu, but I like it everyday more... so I'll try to understand your advices ;) 
Thanks

---

