---
title: "Transistion from Vista to Ubuntu help please?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by crusadera on 2007-11-14
After deciding to not be a part of [ LINK HERE Microsoft's Illegal Monopoly LINK HERE]("http://en.wikipedia.org/wiki/United_States_v._Microsoft") I went to one of the local computer stores to pick a free Ubuntu disk, only to find that both the CDs were corrupt, never the less I IM'ed my friend and used his fast internet connection to download the ISO image and install with that CD, it worked and now im stuck with this blank Ubuntu system I used vista before (came with the laptop)

Now I'm hoping that if any experienced Linux user can help me with the Windows-Linux transition. Like many people before I didnt like Vista's performance too much, but I loved the User interface so much. 

So can anyone help me with any of the following:
Find and or create a User Interface similar to Vista Aero.
Find a Windows Emaluator
Instant Messenger
A way to install WoW
A way to connect to my External Hard Drive

basicly making it similar to vista without it taking up half my RAM

If any of you can help out via replying, phone, instant messaging, email (Runescapeain@hotmail.com)
I would greatly appricate it and I will do my part by spreading the Linux-Ubuntu software.
 -Crusadera

---

### Post by nikolas68 on 2007-11-14
M8 you have a lot of work to do there!!!
My humble suggestion: don't try to emulate Vista and enjoy Ubuntu the way it is!! I bet you'll grow fonder of it...

---

### Post by Dr Small on 2007-11-14
First off, Ubuntu is NOT Vista, so you must first come to that understanding before you can move on. You need to do alot of reading, on the wiki and here at the forum, to solve your problems that you may encounter, and just play around with the system and see what all you can learn about it. ;)

Dr Small

---

### Post by Espreon on 2007-11-14
OK for the WoW thing and if you wanna install other Windows software your gonna need to install WINE, first download the attached  script to your home folder named wine.sh and do this in the terminal:

```

sh wine.sh

```

Then goto your home folder and double click on the wine-doors .deb the script downloaded and install it.

Then goto: Applications>Wine>Wine-Doors

Fill in the info, when its done pop in your WoW CD and look in Wine-Door's list for World of Warcraft, hit install and hit apply.

Then for the IM thing Pidgin is an IM client

For the Aero mock up do the following in the terminal:

```

sudo apt-get install emerald

```

If your using an ATI card (and don't have fglrx installed,  which is the ATI propietary driver do this also:

```

sudo apt-get intall xserver-xgl xorg-driver-fglrx

```

Reboot your system and goto: [www.gnome-look.org](www.gnome-look.org) and hit Beryl and look for a good Aero theme like Linsta.

---

### Post by rhenrick on 2007-11-16
I agree with a previous post ... don't try to dress Ubuntu up as Vista just yet! Play around with what you have right now and have fun with it! Get to learn the OS first.

As with WOW on LINUX ... i tried it with Wine and it worked ... but not too well. Check out Cedega!
Also, check out this site: [www.wowdetox.com](www.wowdetox.com) :)

Anyway, welcome to LINUX and congrats on dropping Microslut Windose!

---

### Post by firedancer on 2007-11-16
> congrats on dropping Microslut Windose!


wow , never heard that before , are you out to kill bill ?:lolflag:

---

