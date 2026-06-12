---
title: "G4 Boot, GLX and Network"
date: 2008-04-07
forum: Apple PPC Users
---

### Post by mikeym on 2008-04-07
Hi,

Sorry about this but I'm finding quite a few problems getting XUbuntu going that I'm not finding answers to myself. I'm trying to install on a G4 Ti 1GHz with Raedon 9000 M256 graphics card.

The first problem I have at the moment is that when I boot it gets as far as the splash screen hangs for 10 minutes then drops me to busybox where I have to type* modeprobe ide-core*. I've followed [these steps]("http://ubuntuforums.org/showpost.php?p=4546107&postcount=1") that seem to be the recomended solution but it's still not working. :confused:

The second issue is with my graphics. I'm getting between 170fps and 9fps on glxgears. It doesn't seem to matter whether I use the "ati" driver or the "raedon" driver. I've tried a few different settings but none seem to be helping.

And finally despite the fact I'm using no security and I was connecting happily I've lost my WiFi network. It happened after a reboot and it just wasn't available. I can see it if I go into manual configuration but it wont let me choose no security from there.

---

### Post by mikeym on 2008-04-07
So to break down my questions a bit further:

[LIST]
[*]**Ide-core** is there something missing from the steps I followed? Could it be a bigger problem with my HD that using modprobe fixes temporarily? Where can I find the errors its encountering?
[*]**Raedon 9000** does anyone have a setup for this that's working? How did you go about it and what packages do you use? What are the modules that you see listed in *xorg.conf*?
[*]**WiFi** Can you use a non-secured WiFi network with XUbuntu? Are there any packages that would cause me to not be able to select a network anymore? (The only thing I was doing before hand is installing a few packages and reverting my *xorg.conf*)
[/LIST]

---

### Post by ssam on 2008-04-07
i recommend you wait for hardy to be released. its a big improvement on my tibook.

it is only a few weeks away. or try the latest test cds [http://cdimage.ubuntu.com/ports/daily-live/](http://cdimage.ubuntu.com/ports/daily-live/)

---

### Post by VCF on 2008-04-07
> **ssam said:**
> i recommend you wait for hardy to be released. its a big improvement on my tibook.

it is only a few weeks away. or try the latest test cds [http://cdimage.ubuntu.com/ports/daily-live/](http://cdimage.ubuntu.com/ports/daily-live/)

Amen on waiting for Hardy, I installed it on my iBook G3/900 (dual USB) with airport & only 384 MB.  Install from live CD went perfectly with no glitches, everything works (including WiFi, sound, video) except for compiz fusion.  Glad I waited as the alphas a month ago were horrible but things have really come up to speed!

---

### Post by slacka-vt on 2008-04-08
Thats really strange. I have the same exact machine and graphics card.
I get an average of 1500fps with glxgears . . . .
 ..  but I'm using Hardy (Development)

Are the drivers any different ?

~s

---

### Post by BladeMelbourne on 2008-04-08
No, the drivers aren't that different - especially performance wise.

Getting glxgears framerates so low is an indication that mikeym's xorg.conf needs some tweaking.

I think slacka-vt's /etc/X11/xorg.conf file will help mikey a lot.

---

### Post by mikeym on 2008-04-09
I'm on hardy now and I'm getting 2000 fps in glxgears. It appears the issue was a gusty one.

---

### Post by stream303 on 2008-04-09
I'm glad to see that.  Kind of wish I had an ati card instead of nvidia..

Are there any further 3D tweaks that can push that performance even better:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

---

