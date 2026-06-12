---
title: "No graphics acceleration at all?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by rj686 on 2007-01-12
I know that without the FGLRX package that their is no 3d acceleration but is ubuntu not detecting something here. I'm getting NO acceleration. Page scrolling is drawing about two fps lol. Anyway isn't it not possible to get AIGLX running on ATI cards at the moment? Is the proprietary ATI driver better than the FGLLRX driver? Just some general re-noob questions. I say re-noob because I've been away for awhile, and running ubuntu on a laptop is WAY different from running it on a laptop :mrgreen:

---

### Post by Delkster on 2007-01-12
> **rj686 said:**
> I know that without the FGLRX package that their is no 3d acceleration but is ubuntu not detecting something here. I'm getting NO acceleration. Page scrolling is drawing about two fps lol.

Which ATI chip or card do you have? Check in the Device Manager or with the 'lspci' terminal command if you don't know.

The open-source radeon driver that is provided with the system and used by default with Radeon cards provides both 2D and 3D acceleration for older Radeon chips but probably not for newer ones yet, and it's not very fast at 3D although it should be quite capable in 2D (normal desktop operation).

> Is the proprietary ATI driver better than the FGLLRX driver?

Fglrx is the proprietary ATI driver.

---

### Post by rj686 on 2007-01-12
lspci gave me:

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c5 :( lol

But I have a Mobility x1600 :)

So no AIGLX for me :(?

I thought there was an open-source driver AND a proprietary driver?

---

### Post by Armor on 2007-01-12
Yes I am having the same problem - I just installed and when I scroll a web page, it goes like 2.32 fps as well. Very choppy. How do I fix this? I have a x1800XT Radeon

---

### Post by Armor on 2007-01-12
"lspci" shows this for my vid card:
> 01:00.0 VGA compatible controller: ATI Technologies Inc R520 [Radeon X1800]
01:00.1 Display controller: ATI Technologies Inc R520 [Radeon X1800] (Secondary)


---

### Post by Delkster on 2007-01-12
> **rj686 said:**
> So no AIGLX for me :(?
I don't really know. I've got the impression that the proprietary driver from ATI doesn't support AIGLX yet, and that is probably the only way of getting 3D acceleration (which is required for desktop effects) on that card.

> I thought there was an open-source driver AND a proprietary driver?

Yes, there are both.

The open source driver comes with every standard Linux distribution and is often referred to as the "radeon" driver because that's the name of the driver module. The open source driver provides 2D support, and for some older ATI chips also 3D acceleration. The 3D part of the open source driver comes from the DRI project, so in that context the open source driver is often referred to as the DRI radeon driver. The open source driver also supports AIGLX for those chips that have 3D support from it.

Fglrx is the proprietary driver from ATI. It supports 3D acceleration for newer cards but, as far as I understand, it doesn't support AIGLX yet. I may be wrong, though, and I don't use either AIGLX or the fglrx driver myself.

I hope that explains things a little.

---

### Post by Delkster on 2007-01-12
> **Armor said:**
> Yes I am having the same problem - I just installed and when I scroll a web page, it goes like 2.32 fps as well. Very choppy. How do I fix this? I have a x1800XT Radeon

If you haven't installed the proprietary ATI driver yet, you may want to try that.
There are [instructions in the Ubuntu wiki](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).

---

### Post by rj686 on 2007-01-12
Yeah I've come to the conclusion that as of now i have NO AIGLX support. I'm running the fglrx drivers at the moment and I can't even get beryl running, but then again i see  AIGLX comes standard with 6.10. As I have an x1600 the open-source drivers aren't compabitble with x1600

---

### Post by mcduck on 2007-01-12
> **rj686 said:**
> lspci gave me:

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c5 :( lol

But I have a Mobility x1600 :)

So no AIGLX for me :(?

I thought there was an open-source driver AND a proprietary driver?

Yes, no AIGLX, but if you install fglrx drivers the card will work just fine. And it runs Compiz/Beryl great too with XGL.. (I have the same card on my laptop)

---

### Post by rj686 on 2007-01-12
Any ETA on when all or at least most ATI cards will support it? ATI doesn't like open source very much do they :(

---

### Post by konst88 on 2007-01-12
Did you checked the option for smooth scrolling in firefox?
And you may use the open source ati driver, for some 3d.

---

### Post by cypher_666 on 2007-01-13
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

imma try and sort this out using the help on here, and hope i dont break X, just thought id chip in (no pun intended)

---

### Post by Patrick-Ruff on 2007-01-16
you can possibly use the open source drivers . . . they only support grapics acceleration for certain cards, mine wasn't one of them (well, it was, but it was only expiremental.)

good luck to you.

---

### Post by Frank Golden on 2007-01-16
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
This is the Wiki from ATi. Works for me. 
Method 2 in edgy installs the latest drivers. I believe the Ubuntu wiki mentioned earlier was derived from this. After install reboot.

---

### Post by melenor on 2007-01-16
i have an ATI X1800 XTX and i am getting no 3D acceleration on it, even small games lag. i know this is not an hardware problem as the card works on windows, is there anywhere i can go to get a driver or find out how to install a driver for this card. could WINE be used to install the ATI driver?

---

### Post by Delkster on 2007-01-16
> **melenor said:**
> i have an ATI X1800 XTX and i am getting no 3D acceleration on it, even small games lag.

Have you tried installing the proprietary ATI driver (dubbed "fglrx")? It's available in Ubuntu but not installed by default so if you don't know whether you've installed it or not, you probably haven't.

The Ubuntu wiki has [instructions for installing and enabling the fglrx driver](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). Look at the "Install from Ubuntu repositories" section.

> could WINE be used to install the ATI driver?

No, it doesn't work for drivers. There are native Linux drivers, the ATI ones just seem to be a little problematic at times.

---

### Post by rj686 on 2007-01-16
Only problem is the open-source ones don't support the x1000 seriers cards :(

---

### Post by Frank Golden on 2007-01-16
> **rj686 said:**
> Only problem is the open-source ones don't support the x1000 seriers cards :(
Again check out 


[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Use method 2 to compile and install.

Follow directions.

---

### Post by rj686 on 2007-01-17
> **Frank Golden said:**
> Again check out 


[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Use method 2 to compile and install.

Follow directions.

I did do that. Those aren't the open source drivers. The open source are the radeon drivers.

---

### Post by cypher_666 on 2007-01-17
just on a side not i tried it and fried my X :( but luckily i was rescued by going on the other box and looking up the problem on here, reconfigured my X server and now all is well again.

this place is cool

---

### Post by Frank Golden on 2007-01-17
> **rj686 said:**
> I did do that. Those aren't the open source drivers. The open source are the radeon drivers.Ok you have officially confused me.
I thought you didn't want the open source drivers. If you have the proprietary drivers installed correctly, according to the directions in the Wiki i mentioned you should have great 3-D and 2-D.

Make sure the following is at the end of your /etc/X11/xorg.conf file.

Section "DRI"
	Mode         0666
EndSection

This allows direct rendering in normal user mode.

Please post output of ```
sudo fglrxinfo
```.

Also ```
sudo glxinfo
```

---

### Post by rj686 on 2007-01-17
My original purpose was to get AIGLX running with my x1600, this thread is at least several days old. Since then I've installed the FGLRX drivers (closed-source) and i get DRI but like others AIGLX is not compatible with FGLRX drivers. :) I hope eventually the open-source drivers come to support the x1000s cards.

---

### Post by Frank Golden on 2007-01-18
> **rj686 said:**
> My original purpose was to get AIGLX running with my x1600, this thread is at least several days old. Since then I've installed the FGLRX drivers (closed-source) and i get DRI but like others AIGLX is not compatible with FGLRX drivers. :) I hope eventually the open-source drivers come to support the x1000s cards.
Don't hold your breath. I think more than likely the closed source drivers will.

---

### Post by DWM007 on 2007-01-24
I too would like to get smooth scrolling, but I have an old machine with build in graphics.
It shows up as 01:00.0 VGA compatible controller: Trident Microsystems Cyber Blade/ iL
Does anyone have any ideas on what drive I should use and where I can get it.

Thanks

---

