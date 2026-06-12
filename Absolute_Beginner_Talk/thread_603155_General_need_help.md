---
title: "General need help"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-04
I have been having a fun last couple of days. I really want to make an honest effort to change to and learn Linux. Over the past couple of days I have gone from Ubuntu, to PCLOS, to Mepis, and even tried Suse. 

So far, Ubuntu has worked the best on my system. There are a couple of things that I don't like about Ubuntu. (1) I don't like the brown. It's got to go. Brown is good for coffee. (2) I don't like everything up at the top of the screen, but I think I could learn to live with that. Heck I've already had to accept that my X-fi sound card is not supported. Thank God for on board sound. 

What I like about Ubuntu is that it seems (so far) to work with my system. It finds my Western Digital 'My Book' and even puts an icon on the desktop. I like that. PCLOS did not find 'My Book' at all. I tried for 2 days to get someone to help me fix that but only 1 person responded in their forums. People here responded quite well on my previous post. PCLOS also gave me some trouble getting my video card set up correctly, and I never did get the default settings for my monitor to work. I have no doubt that if I was patient enough and willing to play around more that I could resolve those problems in PCLOS, but I don't have to in Ubuntu, it pretty much just worked. 

In either system I still haven't gotten as far as running a virtual machine in Linux but I do want to tackle that as well. First I would prefer to just get a system tweaked and working well before I go to that. For instance, dealing with sound files, movie files, and getting my CD collection cataloged is much more important than the virtual machine. 

So, I am going to close out from this live disc now and install Ubuntu. Hopefully by the time I get it installed I can come back to this thread and see what I can do to make my desktop look better. Please help, I really dislike the Microsoft corporation.

---

### Post by drs305 on 2007-11-04
Don't like brown? System, Preferences, Appearance will give you a few choices.

If you don't like the panel at the top, right clickon an empty space on the panel, select Properties, and you can put it on either side or the bottom. If you are taliking about items on the desktop itself, you can hide the volumes by editing the entries using 'gconf-editor'. There are threads on how to do that.

Welcome to Ubuntu.

---

### Post by dpar on 2007-11-04
Ya, make it look any way you like. That's the beauty of Linux.

---

### Post by TeaSwigger on 2007-11-04
That's the important thing, that you enjoy the journey.

If you feel like something different down the road, remember to try kde (via kubuntu if you like) or fluxbox (via fluxbuntu if you like). Good luck to ya :)

---

### Post by zippy028 on 2007-11-04
The Ubuntu forums have tons of info regarding all sorts of customization related to your desktop. The Ubuntu community as a whole is very helpful with getting problems solved and much to their credit and What I consider one the best attributes of the forums is the number of how-tos on the forums eliminating sorting through countless google returns to find what you are looking for. Good luck and have fun with Ubuntu.

---

### Post by bgast1 on 2007-11-04
Thanks, I finally got it installed, again. I have 2 'My Book' icons on the desktop now. Need to get rid of one of them. Getting a different wallpaper up will make a huge difference. Changing the desktop and the way it acted was one of the things that I liked about PCLOS, but not finding all of my hardware was a real mistake. 

I used the proprietary driver for my video card. Was that the right way to go about it. My video card is an ATI X1950 Pro 

By the way PCLOS and the other distros that I have looked at have all been KDE. I don't know anything about Gnome.

---

### Post by dpar on 2007-11-04
You can install the kde desktop in Ubuntu as well if you like that better.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by bgast1 on 2007-11-04
Need to know about the video driver question before I do anything else with the desktop, Using the proprietary driver wouldn't let me install any desktop effects.

---

### Post by SomeGuyDude on 2007-11-04
> **bgast1 said:**
> Thanks, I finally got it installed, again. I have 2 'My Book' icons on the desktop now. Need to get rid of one of them.

I have a Simpletech external HD and ran into this as well. It only happened when I booted up with the HD plugged in and on. When I disconnected, only one icon went away. So I restarted with the thing connected but not turned on, and no problem. Turned it on, one icon. All gravy.

---

### Post by bgast1 on 2007-11-04
Well, I tried to fool around with the drivers and now all I get is a blank screen when I try to boot. Is there a way to fix this without a re-install?

---

### Post by HermanAB on 2007-11-04
I always drag everything from the top panel to the bottom panel and then delete the top panel.  At that point of course, Gnome looks just like KDE, so that is another option - install Kubuntu.

---

### Post by -grubby on 2007-11-04
> Well, I tried to fool around with the drivers and now all I get is a blank screen when I try to boot. Is there a way to fix this without a re-install?

enter this into a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

There might be a better way to change drivers that is easier, but this is kind of the only guaranteed way.

---

### Post by bgast1 on 2007-11-04
Code:

sudo dpkg-reconfigure xserver-xorg

There might be a better way to change drivers that is easier, but this is kind of the only guaranteed way.

How can I do this if I can't get past the blank screen?

---

### Post by -grubby on 2007-11-05
> **bgast1 said:**
> Code:

sudo dpkg-reconfigure xserver-xorg

There might be a better way to change drivers that is easier, but this is kind of the only guaranteed way.

How can I do this if I can't get past the blank screen?

restart and enter into recovery mode, oh,and by the way look at my post and you can hit the "quote" button to quote its in the southeast corner

---

