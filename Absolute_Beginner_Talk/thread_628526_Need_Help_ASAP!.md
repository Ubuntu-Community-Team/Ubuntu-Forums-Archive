---
title: "Need Help ASAP!"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Tristicus on 2007-12-01
Well, I am using an old computer for Linux right now (20gb HDD, P3 processor, 256mb RAM) and it is very old and freezes up sometimes. Well, I was downloading a bunch of updates, and I go to check, and my wireless isn't working. I go to my little manager, and the mouse freezes, and everything froze. So I manually turned off the PC, then re-booted. 

I can boot all the way into the Ubuntu sign in, and then sign in, but then the screen goes blank with the pointer in the middle of an orange screen. I can move the pointer, but nothing else.

What do I do? I do not want to re-install, because I had some things up there I wanted, like my wireless internet working, some bookmarks about that, and a special manager for wireless (WICD or something).

Ubuntu 7.10 Gutsy Gibbons is the Distro.

---

### Post by PmDematagoda on 2007-12-01
I realise that this may not solve your problem directly, but try using Xfce instead of GNOME, it can help reduce the freezes rather drastically. 

You can install it using:-
```

sudo aptitude install xubuntu-desktop
```

It may also solve your problem.

---

### Post by derred on 2007-12-01
It sounds to me like the updates you were doing didn't finish. When you reach the login press ctrl+alt+f1. to go to a text terminal. Login there and when you get:
```
username@localhostname:~$
``` type in ```
sudo apt-get update; sudo apt-get upgrade
``` to continue the upgrade process.

Also I agree with PmDematagoda that XFCE might be better for an older system

---

### Post by Tristicus on 2007-12-01
Going to try that now. Thanks a bunch guys!

---

### Post by Tristicus on 2007-12-01
Man thank you SO MUCH Derred. Posting from Ubuntu now.

To PMDematogota (sp?), if I run/install that, will it wipe my installation or what?

---

### Post by Tristicus on 2007-12-01
Sorry to post again, but I checked around, and the xubuntu or w/e looks like a distribution, so....I am just wary about that before I type in that command.

---

### Post by jken146 on 2007-12-01
Xubuntu is the version of Ubuntu that uses the XFCE window manager.  If you install the package xubuntu-desktop you will be installing the XFCE window manager and some other things that it needs in order to run.  You will be able to choose which window manager to use (XFCE or Gnome) at the log in screen.

---

### Post by Dr Small on 2007-12-01
Xubuntu is a distro, but by installing the xubuntu-desktop on your currennt installation will only install all of the meta packagaes to make the xubuntu-desktop work. It doesn't do the entire filesystem, just xubuntu applications, the xubuntu session, and xfce4.

Dr Small

---

### Post by Tristicus on 2007-12-01
So it will be like having 2 distros on my computer sort of? All my files and settings and programs will still be there though, correct?

---

### Post by jken146 on 2007-12-01
It will be like having 2 window managers in one distro.  All your files will remain, don't worry.

---

### Post by Tristicus on 2007-12-01
Thanks guys!

---

### Post by SunnyRabbiera on 2007-12-01
xubuntu and ubuntu are basically the same, installing the xubuntu desktop will not mess with your system in any real way as at the core they are the same OS.
Xubuntu is a ubuntu variant, but not its own distribution.
you see to appeal to a broader audience ubuntu had spawned off two main branches
kubuntu for KDE users
and Xubuntu for XFCE users.
Ubuntu uses gnome and well not many like it
to understand the difference between them you have to understand desktop environments, the three main ones are KDE, gnome and XFCE.
Unlike windows or apple you have more then one way to manage your systems.
if you dont like gnome, there is kde or xfce as alternatives
all of them do the same thing, but in different ways.
KDE is based off something called qt
and gnome and xfce are based off something called gtk
both of these are the core engines behind most of the apps you see, from the gimp to pidgin and from firefox to evolution is gtk
and applications like amarok and konqueror are qt apps.
now the reason why there are so many is because of a little dispute a few years back, you see the engine of kde qt was not compatible with open source ideals.
as you might know linux is open source and people felt that the price tag and license associated with qt back then was wrong so they created gtk.
now qt is pretty much open source and you can use it freely with no cost as long as you dont sell any software created by it.
anyhow gnome was the first KDE alternative during this time then came XFCE (well technically they are about the same age, but do to its MANY changes its practically a brand new thing every time there is a number change, there is a LOT of difference between version 3 and 4 and so fourth).
XFCE sort of came out on its own, it was once based on CDE another desktop environment with a issue with linux.
anyhow XFCE has pretty much come into its own by now and most feel its lighter then KDE and gnome (as both have been loaded with a lot of junk over the years)

anyhow as I said, installing xubuntu desktop will probably do little to no harm on your system

---

### Post by Dr Small on 2007-12-01
.. And fluxbuntu is even lighter than xubuntu.

---

### Post by Tristicus on 2007-12-01
SO should I run Flux or just Xubuntu? And the command for flux would be 

sudo aptitude-get install fluxbuntu 

or what?

---

### Post by Dr Small on 2007-12-01
Flux may be a little bit more complicated for new users (it is somewhat for me), so you had best try out Xubuntu. It is lightweight, but I was just recommending fluxbuntu since it is lightweight too..

Anyhow, you could install flux too if you want:
```
sudo apt-get install fluxbox
```

---

### Post by Tristicus on 2007-12-01
Okay thanks. I will probably just install Xubuntu

---

### Post by Tristicus on 2007-12-04
Well, I installed Xubuntu and am running in it right now. It is different in some ways, but faster. I like the look of regular Ubuntu better, but this is fine as long as it runs :p

---

### Post by NightCrawler03X on 2007-12-04
If you want more speed, you should run Enlightenment instead of Xfce.
Way faster at less resources used.

plus, it's better at looking awesome when you tweak it

---

### Post by Tristicus on 2007-12-07
Yeah, but I am a big noob right now lawl. I don't know what that is really, or know how to use it. Gnome and Xfce are good for me right now. I like more GUI based at this time.

---

