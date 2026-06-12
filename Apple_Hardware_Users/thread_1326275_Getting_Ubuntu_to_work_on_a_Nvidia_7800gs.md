---
title: "Getting Ubuntu to work on a Nvidia 7800gs"
date: 2009-11-14
forum: Apple Hardware Users
---

### Post by aeromax on 2009-11-14
I have a G5 which I'd like to try Ubuntu on just for kicks, but my display looks terrible, as if I was running in 16 colors or something. I can hardly read anything. However, I don't have an OEM apple graphics card, and instead I'm running a Flashed Nvidia 7800GS that I picked up. It works fine in OSX of course, but I suppose that there are no linux drivers for PPC for this card. Is there anything I can do? I can't even find my xorg.conf file to change settings.

---

### Post by aeromax on 2009-11-15
buuuump!

---

### Post by linuxopjemac on 2009-11-16
try searching the ubuntu forums....there is a search button ;)

[http://ubuntuforums.org/showthread.php?t=1125400&highlight=Nvidia+7800GS](http://ubuntuforums.org/showthread.php?t=1125400&highlight=Nvidia+7800GS)

---

### Post by aeromax on 2009-11-16
Yes true, and I've used it. However, I'm posting in the Apple forum since I'm on PPC, AND using a non-OEM Nvidia card, so drivers may be nonexistant for PPC Linux. I can't just use any old drivers, unless someone tells me a way it will work!

---

### Post by linuxopjemac on 2009-11-16
sorry, I just found out that it is not easy at all for you. You are stuck with the open source nv driver...

[http://ubuntuforums.org/showthread.php?t=288695](http://ubuntuforums.org/showthread.php?t=288695)

this might also be interesting:
[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

here you will find the wiki for configuring nv in xorg.conf:
[http://xorg.freedesktop.org/archive/X11R7.0/doc/html/nv.4.html](http://xorg.freedesktop.org/archive/X11R7.0/doc/html/nv.4.html)

---

### Post by aeromax on 2009-11-16
I'll try those links. But does anyone know why I wouldn't have an xorg.conf file  on my machine? I searched for it, and couldn't find it anywhere.

---

### Post by ZoiaGuyver on 2009-11-16
The xorg.conf file is created once it detects and set's up the card. There should be a sample one in there.

Depending on the Xorg version (im taking it that your using the one from 9.10) you should be able to use the open source nv driver. The flashing shouldn't of been a problem but as far as i know there are no NV drivers at all for PPC arch (atleast not that support the newer cards).

Plus with them being closed source means we cant build them for the arch either..

---

### Post by natgab on 2009-11-16
> **linuxopjemac said:**
> try searching the ubuntu forums....there is a search button ;)

[http://ubuntuforums.org/showthread.php?t=1125400&highlight=Nvidia+7800GS](http://ubuntuforums.org/showthread.php?t=1125400&highlight=Nvidia+7800GS)

---I have to add some advice about searches. It seems that if the thread does not have "tags" added the ubuntu forum search does not always give you results.  Even with several tries.  I have get better results if I enter into google and it points me to the proper thread in Ubuntu forums. Weird, but it has worked.

To aeromax:

I have a Windows 64MB ATI video card that is flashed for Mac in my G4 at work.  I got it on eBay from some guy that sells them already flashed.  And I was able to use the live disc for Breezy Badger 5.10.  I only played around to see if it started, but the screen worked perfect.

I think you should be able to get it working so long as you know that you will have to edit the Xorg.  I am running 9.04 on my Powermac G5 (see below) and it installed straight from the live disc.  But my Powermac does have a stock Apple video card.  good luck

---

### Post by aeromax on 2009-11-16
On my ibook, which I'm using right now, the display is fine and I still don't have an xorg.conf file. I dunno. I'm about to give up on this.

---

### Post by natgab on 2009-11-17
Yeah, my PowerMac that took 9.04 right away has a plain xorg too.  That is everything was detected.  But I edited it to get the 3d acceleration and now I have compiz stuff working.

I had Debian 5.03 working on my iMac, I don't know if you want to have two different systems.  I decided to make them both 'buntus so as not to confuse myself with linux commands, but you might want to try it.

---

### Post by linuxopjemac on 2009-11-17
Aeromax:

You can have you video card detected automatically by a simple command. It should create an Xorg.conf file for you on the fly, which you can adapt later to your needs.

```
sudo dpkg-reconfigure xserver-xorg
```

That was the way for me to get the screen working on my G3 Pismo PowerBook under Debian Lenny.

More info:
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by linuxopjemac on 2009-11-18
any updates ?

---

