---
title: "App Checklist... help me make the switch!"
date: 2010-02-13
forum: Apple Hardware Users
---

### Post by Jheric on 2010-02-13
Let's get one thing straight... I LOVE MY MAC. I even love Mac OS. So what's the point of switching?

I love open software. I love being able to control every bit of my computer. I love linux.

Good reasons, no?

(history: ubuntu 6months, arch 8 months, countless other distros 2+ years)

So! I've put together a checklist of my most treasured Mac Apps to evaluate if I can really make the switch or not. It is ok for me to have to boot to Mac for one, or maybe two things... but if there are too many reasons to stay in Mac OS, I might as well stay there.

This is not a "everything" list. Just the apps I absolutely need to be a productive professional, along with my current understanding of their linux alternatives. Please chime in if my information is incorrect or if you know of a better alternative! I'm sure this could benefit others looking to make a home in their linux partition. 

My Macbook (about a year old) is the target machine. It has a 2ghz core duo, 180gb hd, and 2gb of ram.

> Support for Macbook:
Latest Distros only, install proprietary nvidia drivers
[http://steffenzieger.de/index.php/2009/03/26/why-is-my-macbook-pro-51-getting-so-hot-under-linux/](http://steffenzieger.de/index.php/2009/03/26/why-is-my-macbook-pro-51-getting-so-hot-under-linux/)

Photoshop:
Use gimp with modifications to add support for photoshop features. Some PS versions work in Wine, if necessary.
[http://www.smashingmagazine.com/2009/04/03/8-handy-tweaks-to-make-gimp-replace-photoshop/](http://www.smashingmagazine.com/2009/04/03/8-handy-tweaks-to-make-gimp-replace-photoshop/)

Flash:
Only Version 8 and below works via Wine. No viable native alternatives.

Skitch:
Shutter is a full replacement

Quicksilver:
GnomeDo

iMovie / Premiere:
OpenShot is viable for simple things. But professional video cannot be done on Linux. Premiere and other CS apps may run ok in a VM, possibly.

Video conversions and encoding:
Lots of options. FFmpeg (openshot does a fair bit, as well)

Garageband:
[http://www.jokosher.org](http://www.jokosher.org) is meant as a direct alternative, but is a young program. LMMS, Ardour, Iinux sampler, and Audacity can provide a combined solution, however.

Dropbox:
Linux version available.

Adobe After Effects:
Shake is available for linux but is very expensive and not well-suited for After-effects style animation work. For compositing, however, it is good.

Coda:
No direct alternative with the same feature set. But there are many many "different" alternatives and methods.

Screenflow:
Unsure... but it is unlikely there will ever be a direct alternative to this program and any other OS that is just as smooth and slick for creating professional screencasts. There are many alternatives though, if a quality reduction can be tolerated.

smcFanControl:
mac fanspeed scripts can do this, though not automatically. And not in a program gui.

Cyberduck:
Plenty of ftp apps in linux.

Sleep:
Mac OS sleeps instantly... and wakes almost instantly. I don't know if this can be replicated in Linux or not.



Flash, video, and after effects are the biggest hurdles to full-time linux adoption. I could probably spend 75% of my time in Linux without them... but oh, what a joy it would be if I could escape OS X completely. I don't want to yack about all the reasons why I'd rather be using linux, but suffice to say that I'm tired of the bloat, closed nature, and being held at arm's length from my OS's guts at all times. I'm tinker-happy... and you don't get to tinker much in Mac OS.

---

### Post by Grayer on 2010-02-13
Then why did you buy a mac? You could have easily bought a much cheaper laptop/desktop pc with the same, or even better hardware...because when you buy a mac what you're really paying for is the software...and if you dont use that i dont see what's the point!

---

### Post by tom4everitt on 2010-02-13
> **Grayer said:**
> Then why did you buy a mac? You could have easily bought a much cheaper laptop/desktop pc with the same, or even better hardware...because when you buy a mac what you're really paying for is the software...and if you dont use that i dont see what's the point!

Personally I like to buy macs and run linux on them because of the following reasons:

1. Design.
2. Quality
3. No Microsoft on it.
4. The models are common enough so they're almost always guides on how to fix wireless etc. Buying a random pc and you never know.

And the price different is not that big...

---

### Post by tom4everitt on 2010-02-13
As for your programs:

You don't need to run flash under wine. Simply install it with "sudo apt-get install flashplugin-nonfree" and you get version 10. 

Sleep/wake is not as quick as in os x, but quick enough IMO.

Why don't you try a dual boot for a while?

---

### Post by Jheric on 2010-02-13
I bought a mac because I like Mac OS X more than Windows, I needed a laptop, Macbooks have an excellent design and feature-set, and I appreciate the coherent design of hardware that apple (usually) puts into there machines. I build all my own desktops, but in my experience so far with laptops (about 6 years), I'm not comfortable buying form anyone but Apple at the moment. They may not be perfect, but it's my current preference. 

Besides, if you have to fall back on a dual-boot for closed software... which OS would YOU choose for a media oriented production environment? Certainly not windows... I lost enough projects to instability there than I want to remember.

OS X is a godsend... **when I need it**. I **want** to operate on Linux for my personal OS.

And yes, I intend to use Bootcamp and dual boot. The reason for this post is because I've been out of the OSS loop for about 2-3 years now, and I want to know if there are better alternatives/replacements for the things I listed so I can find out just how far I can get in the Linux environment for work and pleasure.

And I'm with tom4everitt on the pricing... I build my own PCs regularly, and unless you are buying older parts, Apple's machines are very well priced for what they are loaded with, imho. Every laptop I've owned (HP, Dell, IBM, Asus, Acer) has had some defect, design fault, or hardware failure and... though I've heard stories of Macbook woes, I've never seen them. 

Save once, when I brought my machine in 14 months after the purchase with no extended coverage with a failed harddrive and the Apple store saved my data, declared the machine a lemon, and replaced the whole unit with a current model. Why the hell wouldn't I prefer this company? ;)

Well, that's all besides the point anyway. I plan to give my machine a new Ubuntu install later tonight... but I still would like to know any other software recommendations you guys might have.

**EDIT: Oh, and the flash I meantioned in Flash CS4... the production app, not the browser plug-in.**

---

### Post by JohnnyDiamond on 2010-02-13
As far as CS4 goes, I have been trying to find an alternative for a good long time.  If I could get Sibelius and Premiere Pro to run under Linux (Wine or no), I would completely delete windows from my laptop.  

So far, there is no good way to get the functionality under Linux. 

I know they have video editors for Linux, but I really don't like them personally. 
And as for Sibeluis 5, built on .NET... they are working on a workaround, but if Flash CS4 uses anything like that, you are going to have problems. 

I would think that on a good MacBook Pro, you could run VM + Flash when you needed to.

---

### Post by FakeOutdoorsman on 2010-02-13
> **Jheric said:**
> Photoshop:
Use gimp with modifications to add support for photoshop features. Some PS versions work in Wine, if necessary.
I use both GIMP and Photoshop.  I use Photoshop in a virtualized Windows installation running in VirtualBox with no issues.
> **Jheric said:**
> Screenflow:
Unsure... but it is unlikely there will ever be a direct alternative to this program and any other OS that is just as smooth and slick for creating professional screencasts. There are many alternatives though, if a quality reduction can be tolerated.
If you're not adverse to using the command-line, here's a good guide for screencasting:
[url=http://ubuntuforums.org/showthread.php?t=1392026]
HOWTO: Proper Screencasting on Linux[/url]

---

### Post by hollowtd on 2010-02-13
I've had my mac over four years and travel with it and have dual boot and I agree with you, I can't beat it. I trust it and love it and it has never crashed, gotten a virus or ever messed up, once. I love it and PCs cause me headaches like no other. I love linux the most though, for sure. As for programs, you've mentioned even ones I don't know about.

---

### Post by Jheric on 2010-02-14
Alright... so I stayed up all night and go my new Linux partition set up :). Thought I'd give an update.

Linux is awesome.

I've got almost everything exactly the way I like it. The interface is now beautiful, I'm using docky and gnome-do, compiz is set up like expose but with a cool futuristic virtual desktop switcher.

Chrome feels better on Ubuntu than it did on OS X, to be honest.

I installed both Eve Online and Second Life with no issues.

Most of the apps from my checklist are installed.

No hardware issues to report (had to follow a guide for the wireless drivers, but that's it). 

I'm beyond convinced that Ubuntu is ready for the desktop, as far as any competent user is concerned. It's probably still not ready for the completely illiterate user, nor the production media user.

I need to take a crack and tweaking Gimp until it can be a suitable native alternative to Photoshop. I want to avoid running a VM since I only have 2gb of ram.

I'll be running in Linux full time for the next few weeks to see what I can accomplish. So far, I'm extremely pleased though. And my mac is running exceptionally fast, as well.

</rant>

---

### Post by tom4everitt on 2010-02-15
Congratulations! :)

---

