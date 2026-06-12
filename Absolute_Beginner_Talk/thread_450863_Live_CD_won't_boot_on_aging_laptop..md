---
title: "Live CD won't boot on aging laptop."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by cfoley on 2007-05-21
Hi there,

I'm keen to try Linux, mainly out of curiosity but also to see if I can squeeze a little extra performance from my aging laptop. I heard the ubuntu distribution was user friendly enough to be kind to Windows users and I've had a few strong recommendations from various sources.

I downloaded the V7.04 ISO and burned it to disk, hoping to try the live CD for a while before I either eradicate Windows or set up a dual boot. However, during the boot from the CD, the computer froze. I'm sure you're all intimately aware of the boot sequence but here's what I experienced:

I chose the top item from the boot menu.
A scrolling screen of white text appeared.
The GUI loaded with a shaded brown background and a mouse pointer.
To begin with, I could move the mouse but after a certain point in the boot sequence, it froze. I couldn't move the mouse and all disk activity ceased.

I retried this a couple of times, including on safe mode with the same results. I've also tried the Knoppix live CD and experienced a similar problem, leading me to suspect it is a problem with my hardware rather than than an issue with a specific Linux distribution.

I'm using an old (~4 years) Time laptop. Here is the basics of the specs:

BIOS: Insyde Software MobilePRO BIOS Version 3.00.03
Processor: mobile AMD Athlon(tm) 4 1500+ Processor,  MMX,  3DNow, ~1.3GHz
Memory: 224MB RAM (i.e. 256MB with 32MB allocated to the graphics card)

I realise this information is rather incomplete but I'm unsure what you would need to know or where to look. If you think more information would be useful then I'll happily dig a little deeper.

Thanks in advance for your help!

---

### Post by overdrank on 2007-05-21
> **cfoley said:**
> Hi there,

I'm keen to try Linux, mainly out of curiosity but also to see if I can squeeze a little extra performance from my aging laptop. I heard the ubuntu distribution was user friendly enough to be kind to Windows users and I've had a few strong recommendations from various sources.

I downloaded the V7.04 ISO and burned it to disk, hoping to try the live CD for a while before I either eradicate Windows or set up a dual boot. However, during the boot from the CD, the computer froze. I'm sure you're all intimately aware of the boot sequence but here's what I experienced:

I chose the top item from the boot menu.
A scrolling screen of white text appeared.
The GUI loaded with a shaded brown background and a mouse pointer.
To begin with, I could move the mouse but after a certain point in the boot sequence, it froze. I couldn't move the mouse and all disk activity ceased.

I retried this a couple of times, including on safe mode with the same results. I've also tried the Knoppix live CD and experienced a similar problem, leading me to suspect it is a problem with my hardware rather than than an issue with a specific Linux distribution.

I'm using an old (~4 years) Time laptop. Here is the basics of the specs:

BIOS: Insyde Software MobilePRO BIOS Version 3.00.03
Processor: mobile AMD Athlon(tm) 4 1500+ Processor,  MMX,  3DNow, ~1.3GHz
Memory: 224MB RAM (i.e. 256MB with 32MB allocated to the graphics card)

I realise this information is rather incomplete but I'm unsure what you would need to know or where to look. If you think more information would be useful then I'll happily dig a little deeper.

Thanks in advance for your help!

Hi and welcome, the specs on the system should run ubuntu fine. I would suggest trying the alternate cd found here
[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)
Scroll down to the alternate cd and burn it using the "how to" found here
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Hope this works and again welcome and good luck! :D

---

### Post by blazercist on 2007-05-21
you don't have enough RAM, i suggest you use the alternative CD if you are sure you want to install ubuntu as there is no live mode on the alternative CD just an installer.  Also on a dinosaur like that I would suggest a lighter distro perhaps DSL...

---

### Post by Terl on 2007-05-21
> **cfoley said:**
> Hi there,
BIOS: Insyde Software MobilePRO BIOS Version 3.00.03
Processor: mobile AMD Athlon(tm) 4 1500+ Processor,  MMX,  3DNow, ~1.3GHz
Memory: 224MB RAM (i.e. 256MB with 32MB allocated to the graphics card)

I realise this information is rather incomplete but I'm unsure what you would need to know or where to look. If you think more information would be useful then I'll happily dig a little deeper.

Thanks in advance for your help!

The Ubuntu live cd needs 256MB ram as a minimum.  Unfortunately you actually have less than that due to the graphics card cutting into it.  But, you could try [Xubuntu]("http://www.xubuntu.org/").  It is Ubuntu with a lighter weight windows manager.  I think you would be pleased with the XFCE desktop.

I use this on my older hardware also.  It kind of rejuvenates it.  ;)

---

### Post by cfoley on 2007-05-21
Ah. How embarrasing. It's right on the download page.

Thanks for the help and advice. I tried DSL (I'm posting from it right now) but I'd prefer something more fully-featured with more recent software, though I've got an even older compter that DSL should run quite nicely on.

Xubuntu looks far more suitable for my laptop. It's bed time for me just now so I'll give it a spin tomorrow. Thanks for your help everyone and I'll let you know how I get on.

---

### Post by cfoley on 2007-05-22
OK, I tried Xubuntu this morning but is has exactly the same problem (except with a light blue screen this time.) Something that I found curious was that it the startup screen still said "Starting GNOME Display Manager..." I was under the impression that Xubuntu used Xfce instead. Is this simply a case of the output not being changed to reflect the rest of the programming or could there be something wrong with the ISO I downloaded?

Thanks again for any help.

---

### Post by Terl on 2007-05-22
I am not positive but they may have used gdm with XFCE as the desktop.  

Anyway, take a look at [Zenwalk]("http://www.zenwalk.org/").  It uses xfce and is more well featured than Damn Small.  It is slackware based instead of debian based but it is easy to learn, is well documented and has a helpful community.

---

### Post by Brinstar on 2007-05-23
> **Terl said:**
> I am not positive but they may have used gdm with XFCE as the desktop.  

Anyway, take a look at [Zenwalk]("http://www.zenwalk.org/").  It uses xfce and is more well featured than Damn Small.  It is slackware based instead of debian based but it is easy to learn, is well documented and has a helpful community.

I second the suggestion to use ZW, it is a pretty amazing distro for 450mb~.

---

### Post by cfoley on 2007-05-23
I've downloaded Zenwalk and it boots fine from the Live CD. I've played around with it for a bit and think it's the one I'm going to go for.

Thanks again for the help. I'm particularly impressed that you're happy to recommend other distributions that might suit my "dinosaur" better.

---

