---
title: "Can I Install Ubuntu 7.10 with these specs?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by jenson on 2007-11-01
Hi Guys,

I'm currently running a Toshiba Satellite M30, Pentium Centrino 1.5Ghz processor, 512MB RAM, nVidia Geforce FX Go 5200 32MB graphic card, 40GB Hard Disk. 

I have Ubunt 7.04 installed and running smoothly, with the new upgrades available to Ubuntu 7.10, I'm not sure my existing graphic card can still support it or not.

When I downloaded the Desktop CD and burn it onto a CD, I try to run the LiveCD, when it finished loading everything and loading the login screen, I can see nothing there, only some graphical lines across the screen with some background loading music, then that's it, I can't even see what's on the screen, but lines and dots with almost the same colour all over my screen.

Anyone can help me on this?

Thanks.

Regards,
Jenson

---

### Post by Wiebelhaus on 2007-11-01
Try safe graphics mode , But honestly I'd try something alittle more light weight like:

[PCLinuxOS]("http://www.pclinuxos.com/")

[Xubuntu]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.xubuntu.org%2F&ei=LcopR6GxEIvsgwTp8PGPAQ&usg=AFQjCNFaPFp5qcuZB1DJjwMMmKvAswB-_Q&sig2=nQf5L-qDo0J4EkcN1_nbRQ")


[Fluxbuntu]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Ffluxbuntu.org%2F&ei=1MkpR6qMH4jagASJtuSEAQ&usg=AFQjCNFVbQVIdSzCAp3lMIdGJpbzt42_aA&sig2=5JSEHymBhGr2Ai-vEok6_Q")

Or this later today [GOS]("http://www.thinkgos.com/index.html")

---

### Post by Pumalite on 2007-11-01
If you have a working system that you like; stick to it.

---

### Post by AndyCooll on 2007-11-01
You certainly can. I have laptops running at half that speed and with a fraction of that memory and hard drive space and they run a full version of Ubuntu fine. Not fast, but fine for surfing the net, e-mail, music etc.

In your case, you're having problems with your video card settings not being recognised properly. You may need to go to a virtual desktop (press ALT+F1 or ALT+F2 etc through to 6), login and then type:

```
sudo dpkg-reconfigure xserver-xorg
```

Work your way through that wizard, but at the graphics card section choose VESA. This is a bog standard video card driver that works with almost everything. It will at least get you up and running.

When you've finished type:

```
startx
``` 

:cool:

---

### Post by jenson on 2007-11-01
Alright guys, actually I'm trying to get a better support from Ubuntu 7.10, seems like I would have no luck upgrading to it now. Have to stick to my Ubuntu Feisty Fawn 7.04 still.

Hmm, anyway, thanks for the feedbacks guys ;)

Cheers!

Regards,
Jenson

---

### Post by jenson on 2007-11-01
> **AndyCooll said:**
> You certainly can. I have laptops running at half that speed and with a fraction of that memory and hard drive space and they run a full version of Ubuntu fine. Not fast, but fine for surfing the net, e-mail, music etc.

In your case, you're having problems with your screen settings. You may need to go to a virtual desktop (press ALT+F1 or ALT+F2 etc through to 6), login and then type:

```
sudo dpkg-reconfigure xserver-xorg
```

Work your way through that wizard, but at the graphics card section choose VESA. This is a bog standard video card driver that works with almost everything. It will at least get you up and running.

When you've finished type:

```
startx
``` 

:cool:

Hi Andy,

Thanks for the reply. Thanks for telling me these! Looks like I'm still having chance to have it up and running just that I have to use the VESA graphic driver for my graphic cards? I think it only supports up to 1024 x 768? Currently, I'm running 1280 x 800 well on Ubuntu 7.04.

Regards,
Jenson

---

### Post by AndyCooll on 2007-11-01
Well, you don't necessarily have to stick to VESA, I suggest it as starting point, as something to get you going. Once you've got a display you can then play around and find settings that work better in the knowledge that you have a display setting that works and that you can fall back on if you accidentally bork it.

:cool:

---

### Post by Arthur Archnix on 2007-11-01
Make sure you do a search of launchpad and the forums here for your video card first. Your specs are fine, should run nicely, but I've noticed a few people experiencing regressions and issues with 3d rendering in Gutsy. So make sure you card isn't unduly affected. 

One or two posts is to be expected, but if you come across a thread with 10 or 20 then stick with Feisty.

---

### Post by potentia on 2007-11-01
Sure, it will run nicely. If it doesn't, try Xubuntu. But Gutsy isn't a mandatory update, actually you can live without it easily.

---

### Post by Flying caveman on 2007-11-01
Agree.  It should run fine,  A little more RAM would help.   I'm not sure if your "Centrino" is a Pentium M or a Celeron M.  but it doesn't really matter (depends on the apps your running) The only difference is the L2 cache.  Yes, I know Intel will tell you that you have to get the Pentium M to use the "speedstep technology" but it works with the Celeron M too.... just not in Windows.

---

### Post by ozylog on 2007-11-01
absolutely you can...my specs is worse than you and gutsy running smoothly in my computer...

thanks to andycoll....

---

### Post by jenson on 2007-11-05
> **Flying caveman said:**
> Agree.  It should run fine,  A little more RAM would help.   I'm not sure if your "Centrino" is a Pentium M or a Celeron M.  but it doesn't really matter (depends on the apps your running) The only difference is the L2 cache.  Yes, I know Intel will tell you that you have to get the Pentium M to use the "speedstep technology" but it works with the Celeron M too.... just not in Windows.

Hi Flying Caveman and guys,

Sorry for the late reply. Wasn't free to visit this forum for the past few days. It's a Pentium M processor. I haven't have the time to try out the upgrade yet as it always take forever to upgrade and I dont know why, even though the repository is the nearest to my place.

Have been trying to follow this thread and check out what options I can try. 

I will read through and post a comment again. I havent receive my CD yet, i Know it;s not an mandatory upgrade, but I thought it would better support my hardware or so? Not so sure. Hmm.,. seems like 7.10 require higher requirements?

Just wanna to try out latest Ubuntu and see how well does it go. Hehe..maybe I'm just being too itchy fingers :p

Regards,
Jenson

---

### Post by jenson on 2007-11-05
> **ozylog said:**
> absolutely you can...my specs is worse than you and gutsy running smoothly in my computer...

thanks to andycoll....

Wow, that;s cool. I will try this out when I'm free any day within this week =)

Will update you, seems like I need to get to download another copy of Gutsy CD? Geesh..not sure whether my first download is giving me any problem or not..

---

### Post by Pumalite on 2007-11-05
Upgrade is done with the Alternate CD.

---

### Post by jenson on 2007-11-06
> **Pumalite said:**
> Upgrade is done with the Alternate CD.

Alright I will try Alternate CD instead of "live" update from repository or so. First time I burn wrongly so I totally ignore the disc. I'm going to re-download the alternate CD again and see how it goes later. 

Hmm..seems like more people are supporting OpenSUSE? I would like to see Ubuntu become one of the top choice in distributing with laptop or PC or Server purchases though =)

That's unfair to ignore Ubuntu, I personally like it. Hehe... Long live to Ubuntu.

Regards,
Jenson

---

