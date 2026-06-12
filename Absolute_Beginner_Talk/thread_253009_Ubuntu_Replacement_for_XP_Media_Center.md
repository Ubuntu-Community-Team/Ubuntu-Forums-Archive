---
title: "Ubuntu Replacement for XP Media Center"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Penzao on 2006-09-07
Hey guys i was wondering if any one knows of a sutable replacemnt for Windows XP Media Cneter Edition. I have a TV tuner on my card so with Media Center i am able to watch TV right from my computer, this is a major plus because i do not have a TV in my room.

Anyway i was wondering if there is a program of some sort that will allow me to control the TV tuner and allow me to watch tv with it. 

Thanks for your help!:D

---

### Post by orb9220 on 2006-09-07
I think mythTV might be want you want.

---

### Post by Sef on 2006-09-07
Here's a website or two on mythtv.

[http://www.mythtv.org/]("http://www.mythtv.org/")

[http://en.wikipedia.org/wiki/MythTV]("http://en.wikipedia.org/wiki/MythTV")

---

### Post by jonny on 2006-09-07
There are several programs you could use.

Probably the best is MythTV, although setting it up can be a little complex if you're unfamiliar with Linux.  The biggest hurdles are tuning your card, setting up a channel database and grabbing schedule information for your country.

It provides full media centre functionality, although I personally just use the TV and associated scheduling functions, and the video  library management features.  I hardly ever use a real TV any more, as MythTV automatically records my favourite programs so I can watch them without commercials at a time that suits me.

MythTV can easily be set up as a distributed system.  If you have a home network, you can have as many tuner cards in as many PCs as you like, and MythTV will automatically use and schedule the most appropriate hardware.  It's extremely easy to add additional clients so you can, for example, sip a beer in the garden while you're watching live football being streamed to your laptop.

---

### Post by easyease on 2006-09-07
if its a digital tv card theres a strong chance kaffeine player will be able to tune it and let youy watch and record tv easily, you may need to apt-get the kaffeine-xine plug in through synaptic.

---

### Post by Jose Catre-Vandis on 2006-09-07
If you just want a straight forward, full screen, standalone Media Center, try GeexBox
```
www.geexbox.org
```

---

### Post by Penzao on 2006-09-07
thats for the sugestions. MythTV is totaly stupid, impossible to install between the database and drivers. I think i will go try the other suggestions ;)

---

### Post by Penzao on 2006-09-07
umm ok now i have a problem, everytime i install a package it says this at the end

```
E: mythtv-database: subprocess post-installation script returned error exit status 1
E: mythtv: dependency problems - leaving unconfigured
```

---

### Post by Jose Catre-Vandis on 2006-09-08
> **Penzao said:**
> thats for the sugestions. MythTV is totaly stupid, impossible to install between the database and drivers. I think i will go try the other suggestions ;)


and then you go and try to install Myth TV anyway :lol:

---

### Post by dreamsayer on 2006-09-08
> **Penzao said:**
> thats for the sugestions. MythTV is totaly stupid, impossible to install between the database and drivers. I think i will go try the other suggestions ;)

I agree! I tried to install it, followed the instruction carefully, but I couldn't get past the stupid setup screen. So I gave up! This  seems to be one of the most difficult if not pita packages to install for newbs like me. But even tho a newb, I'm getting pretty good at figuring most stuff out!;) 

It would be nice if there was an easy to install solution that worked like Media Center in XP. To watch DVD's, TV, record shows and even use my remote control to power down or put the computer to sleep. 

It is for this reason that I will keep a dual boot copy of Windows around so I can perform these functions until there is an easy to use and install Linux solution.

---

### Post by Fully216 on 2006-09-08
You also have the option of using freevo, an open source home theatre platform similar to mythtv.  I have not personally used it, but I plan to in the near future for my home built PVR.  I know for a fact it has been installed on ubuntu (breazy and up) and many other distros.  I am not sure of the specific support for you tv capture card, but I would check the website and wiki for details.

[http://freevo.sourceforge.net/](http://freevo.sourceforge.net/)

---

### Post by Fully216 on 2006-09-08
Did you try installing mythtv via the synatic package manager?  Version 0.18.1 is available.  Unless you want to latest/greatest release, you can probably fix your installation problems by using SPM.  It sounds like you have/had a dependecy issue, which you won't have to worry about using the SPM.  Just do a quick search for 'mythtv' and chose reinstall.

---

### Post by Penzao on 2006-09-08
thanks for the idea. testing now

---

