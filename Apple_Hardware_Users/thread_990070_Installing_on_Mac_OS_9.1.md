---
title: "Installing on Mac OS 9.1"
date: 2008-11-22
forum: Apple Hardware Users
---

### Post by alphadelta14 on 2008-11-22
i am running a 350 MHz G3 blue PowerPC iMac with 640 MB RAM. i would like to install a version of Ubuntu on it, although it can be anything really. 
i need to do all of my downloads and whatnot on my windows because my mac can not do anything on the internet. it also cannot burn because it has a CD-ROM drive. i do not know anything about these terminal commands. i cannot even boot from any of these disks that i have made. 
Much help is needed and appreciated.
~Thanks in Advance

---

### Post by cuvtixo on 2008-11-22
I'm having my own problems now with ubuntu 8.1 recognizing my cd drive on my G3 ibook. I guess it is an old mitsumi cdrom. It is perhaps "module cdrom0" or cdrom1 instead of plain module name "cdrom"???  This is something to watch out for.

I know with ppc Xubuntu 7.04 I had problems finding the correct update servers in the software source settings.  I guess now PPC isn't officially supported and the default locations for finding updates doesn't work. I'm thinking a brand new install will be easier, but this PPC ubuntu isn't nearly as easy as Intel ubuntu.  
You should also look into Open Firmware, mac ppc's version of BIOS.
This has been very helpful to me, and I've done some easy boot problem fixes with it.   

It might be a heck of a lot easier to find an old OSX 10.3 or 10.4 release on ebay or Amazon or something.  If you're not willing to take a lot of time and learn,

---

### Post by alphadelta14 on 2008-11-22
well, i am pretty sure that my cd drive is device 1. i have no clue as to what Open Firmware is. i can never get a good desciption. and the whole point is to get ubuntu without having to upgrade anything. and i am quite willing to learn if someone is willing to teach.

---

### Post by stream303 on 2008-11-22
> **alphadelta14 said:**
> and the whole point is to get ubuntu without having to upgrade anything. and i am quite willing to learn if someone is willing to teach.

The first thing you'll want to consider is that even if everything were to install just fine, in the end your G3 mac would act roughly the same as a 700mhz Intel box with 640mb ram.  (you double the listed speed for G3's as a comparison).  This might not be enough horsepower for what you want to do.

Unfortunately, Apple ppc hardware isn't designed to cooperate well with Linux probing during installation, as Apple relies quite a bit on internal databases during install to configure the hardware.  The Linux installer would have to adopt that method to make things easier for us, but that isn't likely. :)

That means that as end users, we have to go in and modify configuration files ourselves, based on previous knowledge - which is counterpoint to the whole Mac experience.  Thus the Mac becomes just a regular computer that has enough necessary components to do the job, albeit without 3D, flash etc.  It isn't the fault of Linux that hardware vendors don't provide enough documentation for the programmers to act upon.  It takes a lot of hard work to get Apple hardware working when it doesn't talk back. :)

These faqs and threads should help you get started, especially these:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

What it really comes down to is you have to really want to put Linux on your Mac, and have to put in some time learning techniques and reading other user's solutions in the threads, usually at the commandline, otherwise at the first sign of trouble, you're sunk.  Getting acquainted with vi or nano is highly recommended.  If you have an osx installation already, you can get familiar with these editors in the terminal.

So pick a release, perhaps Hardy 8.04 for your box, and go to town.  You may want to become familiar with your hardware at

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

From that, you'll be better able to determine what kernel parameters you'll need to pass at the second-stage boot: prompt, such as

```
Linux video=ofonly nosplash
```

If you have a radeon card, you may need to add a few more parameters.  When they work, you can add them to your /etc/yaboot.conf file so you won't have to enter them again at boot time.

I wish it were easier, but that's just the way it is.  It might be better to look upon it as a puzzle or adventure.  It might take awhile, but the rewards are worth it.

---

### Post by alphadelta14 on 2008-11-22
i don't have os x and i don't want it. i do however want ubuntu. and for the power, that is plenty enough for me.

the main issue, it seems, is that i don't know anything about those codes; i have never been able to even bring them up.

---

### Post by cuvtixo on 2008-11-22
[http://www.debian.org/releases/stable/powerpc/ch05s01.html.en#boot-](http://www.debian.org/releases/stable/powerpc/ch05s01.html.en#boot-)
[http://www.debian.org/releases/stable/powerpc/ch05s01.html.en#boot-]("http://www.debian.org/releases/stable/powerpc/ch05s01.html.en#boot-")

The above link has been helpful.  In fact there are probably quite a few more PowerPC G3 users with Debian than with flavors of ubuntu.  
Automatic hardware probing might not be perfect, but hardware from ~2001 should not be that difficult to get info/settings for!!! I have found lots of stuff for ibooks and powerbooks with the Synaptic Package Manager-- a very easy extra step after installation.

As far as what the latest linux can do...
Web browsing and email and mp3 playing are not very demanding, and the G3 should be able to do this on the latest linux releases.  The OP has been using Mac OS 9.1 for goodness sake!!! <on soapbox> If the latest Ubuntu can not outperform Mac OS, it is because of lack of will.  There are plenty of other distros out there! Debian calls Firefox Iceweasle, that's the biggest difference, and I may just stick with them if Ubuntu continues to be lame about G3 support <off soapbox>

---

