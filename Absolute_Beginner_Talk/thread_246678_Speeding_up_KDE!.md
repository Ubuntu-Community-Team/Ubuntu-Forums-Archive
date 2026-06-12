---
title: "Speeding up KDE!"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-08-29
Hi,

I have almost no experience with Kubuntu, since I use Ubuntu almost exclusively (except for servers, Debian ftw).

I just installed Kubuntu onto a 500mhz P3 with 256mb ram. I realize this machine is not top of the line by any stretch, but KDE does seem to run pretty well on it.

Of course, there are always room for improvements. :)

In your opinion(s), what are the biggest changes that I can make to speed up this system?

This machine will basically just be a workstation for testing compiled apps (no sound stuff necessary, no printer support necessary, etc.).

Thanks!

---

### Post by IYY on 2006-08-29
The best way to speed KDE up is to use IceWM or Fluxbox instead. ;)

However, I think you can use lighter themes, add more than one preload instance of Konqueror, and disable opaque window moving and resizing.

---

### Post by DarthMandeep on 2006-08-29
The single biggest change I can think of would be to use something like JWM or IceWM instead of loading all of KDE.

If you really want to use KDE I'd look into basic system speed tweaks (making sure DMA is on, prelinking, hdparm, etc.) and KDE-specific tweaks like using lightweight themes.

My laptop has lower specs than yours and runs fine as a general web-browsing, emailing, IMing box using JWM and light apps.

---

### Post by PPAAUULL on 2006-08-29
I would think that there is not a lot of things that you could take off of KDE seeing as when you installed it it was just a the basics and nothing really added in that slows it down. I would just change to fluxbox or something like that to speed it up if you want to that badly.

Paul

---

### Post by justin whitaker on 2006-08-29
It seems like everyone is not answering your questions, but they are absolutely right: Kubuntu's KDE is pretty basic as far as KDE installs go....

---

### Post by Kurt` on 2006-08-29
I knew I'd get a ton of recommendations against it, but I *am* testing an application I'm developing in KDE... or I would have gone with something else from the start. :p

I was looking more for tweaks/settings changes that would remove anything that I really don't need... aside from basic stuff (killing unneeded services, using lightweight themes, etc.)

This is my only spare computer too, I don't feel like using VMWare on my main desktop.

---

### Post by aysiu on 2006-08-29
I would do ```
sudo aptitude update
sudo aptitude install kpersonalizer
kpersonalizer
``` and disable everything except image previews and background wallpaper.

---

### Post by telegramsam on 2006-08-29
> **aysiu said:**
> I would do ```
sudo aptitude update
sudo aptitude install kpersonalizer
kpersonalizer
``` and disable everything except image previews and background wallpaper.

Is there an equivalent to this in Gnome?  I'm running a 600Mhz processor and 256MB of RAM.  It's not S L O W, but it's not lightning fast either.  New build is underway..:-D  but in the meantime..

---

### Post by aysiu on 2006-08-29
> **telegramsam said:**
> Is there an equivalent to this in Gnome?  I'm running a 600Mhz processor and 256MB of RAM.  It's not S L O W, but it's not lightning fast either.  New build is underway..:-D  but in the meantime..
I don't think there is one for Gnome.

---

### Post by Omnios on 2006-08-29
I ran KDE on a P2-350 with 256megs of ram and it ran about the same as win98. Another thing  Iread was the actual Kubuntu CD install supposidly runs faster than just adding KDE to Ubuntu. Also there is a KDE config where you can turn off a lot of the eye candy and it will run pretty well on 500mhz

---

### Post by Kurt` on 2006-08-29
Thanks! I had forgotten about kpersonalizer.

I must say, KDE does run much faster on this machine that I anticipated. Much more so than XP ever could. :p

---

