---
title: "Best OS for Compaq Presario 1230 Laptop (233MHz/32MB)"
date: 2012-08-19
forum: Any Other OS
---

### Post by NekoMaster on 2012-08-19
Heres a link to the Compaq presario 1230's spec's [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00255302](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00255302)

I just got this thing today, saved it from going into the dump. It's an OK laptop, and its rather responsive for a 233MHz Cyrix CPU and 32MB SDRAM (SoDIMM Style). I have no way to upgrade any part of this thing (though I wish I had of saved the RAM from the 1210 I use to have)

So I was wondering if there's anything aside from Windows 98. I don't care if it's spartan in the looks (in terms of GUI) but I need something that can support a USB Wifi Adapter (Zydas 1211B). It also has to fit on a 3.2GB Hard drive and work with 233MHz and 32MB RAM (though I know about swap files/page files)

If there's anything out there that can work on this dinosaur of a laptop then I'd like to hear it.

---

### Post by NekoMaster on 2012-08-20
So, any suggestions people?

---

### Post by black veils on 2012-08-20
[damn small linux]("http://damnsmalllinux.org/")

---

### Post by Petro Dawg on 2012-08-20
I personally like [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm").

I haven't tried Damn Small yet, it may be ok.

If you want something mostly for web browsing you can give [Browser Linux]("http://www.browserlinux.com/") a try.
  
Make live CD's for all and try them.

---

### Post by kurt18947 on 2012-08-20
I got a puppy live session to load on an old HP Celeron with 64 MB. RAM but there was only like 32 k free once it was loaded.  32 MB. ain't much.

---

### Post by NekoMaster on 2012-08-20
I havent tried DSL yet, and Windows 98 SE either freezes when loading after I install it, or it gives me a missing VMM32.VXD error.

Also, puppy linux hangs on "Loading Kernal..." on my laptop.

Is there nothing I can put on this peice of crap?

---

### Post by pqwoerituytrueiwoq on 2012-08-20
dsl is your best bet, or a older copy of puppy

---

### Post by Petro Dawg on 2012-08-20
> **kurt18947 said:**
> I got a puppy live session to load on an old HP Celeron with 64 MB. RAM but there was only like 32 k free once it was loaded.  32 MB. ain't much.


I think puppy demands less RAM once it is installed on the HD.  While it running "live" it uses more RAM than it does on full install.  

Yeah, and 64MB aint much either

---

### Post by Petro Dawg on 2012-08-20
> **NekoMaster said:**
> I havent tried DSL yet, and Windows 98 SE either freezes when loading after I install it, or it gives me a missing VMM32.VXD error.

Also, puppy linux hangs on "Loading Kernal..." on my laptop.

Is there nothing I can put on this peice of crap?


How long did you give Puppy?   It can take a long time for Kernel to load, especially when on a very low ram system.  Once you get it running and have it installed on the hard drive it will boot quickly (hopefully).

---

### Post by NekoMaster on 2012-08-20
> **Petro Dawg said:**
> How long did you give Puppy?   It can take a long time for Kernel to load, especially when on a very low ram system.  Once you get it running and have it installed on the hard drive it will boot quickly (hopefully).

I think i gave it about 10 minutes. I tried 4.2.1 and 4.3.1

Whats the lowest version of Puppy linux (or linux kernal) that supports a ZyDas 1211B USB WLAN card? It seems that DSL does not have the driver for it.

---

### Post by Petro Dawg on 2012-08-21
> **NekoMaster said:**
> I think i gave it about 10 minutes. I tried 4.2.1 and 4.3.1

Whats the lowest version of Puppy linux (or linux kernal) that supports a ZyDas 1211B USB WLAN card? It seems that DSL does not have the driver for it.

I don't know much about older versions of Puppy.

Do you have another computer (with more RAM) that you could place the Hard Drive into, do the full install, and then put the Hard Drive back into the low RAM computer.  I think your RAM is just too low to run a live version of anything currently out there?   

Have you tried [Browser Linux]("http://www.browserlinux.com/")?  It might use a little less RAM.

---

### Post by Petro Dawg on 2012-08-21
I found a distribution called [ttylinux]("http://ttylinux.net/"), I've never tried it before, but it looks like there are about 6 distributions to choose from.  I believe these use a command line interface only and are supposed to be able to run on as little as 28MB RAM.

You'll probably have to use Lynx (text based web browser) to surf the web, and you would have to become more familiar than I am at terminal commands.  I'm sure it would require some additional research,  but definitely a fun project if you are up to it.

---

### Post by NekoMaster on 2012-08-22
> **Petro Dawg said:**
> I found a distribution called [ttylinux]("http://ttylinux.net/"), I've never tried it before, but it looks like there are about 6 distributions to choose from.  I believe these use a command line interface only and are supposed to be able to run on as little as 28MB RAM.

You'll probably have to use Lynx (text based web browser) to surf the web, and you would have to become more familiar than I am at terminal commands.  I'm sure it would require some additional research,  but definitely a fun project if you are up to it.

I don't like command line only OS'es because theres usually no support for mice and its hard to get games running. Also this laptop may be used by my sister and she's a total noob when it comes to linux.

For now I installed Windows 98 but browsing on it is really really slow, and most of the time websites dont load up in Internet explorer 6 (which is to be expected since it doesnt support all the new stuff)

---

### Post by lykwydchykyn on 2012-08-23
I'll save you some time here:  You are *not* going to get a satisfactory Linux-with-X11 experience on this hardware.  No distro will give it to you.

DSL is pretty much the only hope you have if you want Linux, and even then there just isn't a lot of linux software that's going to run on that little amount of RAM.

FreeDOS might be an option; It has a GUI that makes Windows 98 look futuristic, or you can run it command-line; but it's supposedly fully DOS compatible, and there is a treasure trove of old DOS freeware floating about the 'net (not to mention the attics and garages of anyone over 30).

I don't think AROS, Haiku, Syllable, or any of the other crop of new non-Linux free OS's will run on that hardware.  Menuet or KolibriOS might, but if you find anything useful to do on those systems you're doing better than I am.

EDIT: Actually, check out [LightDOS](http://lightdos.wordpress.com).  It's a FreeDOS distribution that comes with a nice, reasonably modernish desktop.  It's system requirements fit your hardware, and it's only a 6MB iso.

EDIT2: DOScore, a.k.a. Aura is another DOS-based option.

---

### Post by Random20210831 on 2012-08-23
Puppy Linux are best for your laptop.

---

### Post by angryfirelord on 2012-08-25
The newer distros today are going to have a hard time running on 1990s hardware. I'd say first try a Debian minimal install and see if you can use something like IceWM.

If you're feeling ambitious, OpenBSD is another choice.

---

### Post by ?#Yhf%*&amp; on 2012-10-29
> **lykwydchykyn said:**
> I'll save you some time here:  You are *not* going to get a satisfactory Linux-with-X11 experience on this hardware.  No distro will give it to you.

DSL is pretty much the only hope you have if you want Linux, and even then there just isn't a lot of linux software that's going to run on that little amount of RAM.

FreeDOS might be an option; It has a GUI that makes Windows 98 look futuristic, or you can run it command-line; but it's supposedly fully DOS compatible, and there is a treasure trove of old DOS freeware floating about the 'net (not to mention the attics and garages of anyone over 30).

I don't think AROS, Haiku, Syllable, or any of the other crop of new non-Linux free OS's will run on that hardware.  Menuet or KolibriOS might, but if you find anything useful to do on those systems you're doing better than I am.

EDIT: Actually, check out [LightDOS]("http://lightdos.wordpress.com").  It's a FreeDOS distribution that comes with a nice, reasonably modernish desktop.  It's system requirements fit your hardware, and it's only a 6MB iso.

EDIT2: DOScore, a.k.a. Aura is another DOS-based option.

As the developer of LightDOS, I would have to say it's not quite ready for anything more than emulator use. The only way to install it at the moment is to write the USB image to a hard disk. But you are more than welcome to test it :D

---

### Post by doorknob60 on 2012-10-31
Any modern distro or kernel will have a hard time running with only 32 MB of RAM. I had a similar Compaq with 64 MB of RAM, and even 4 years ago when I was trying to put Linux on it, everything with a 2.6 kernel used too much RAM for comfort. DSL was the only one that ran decently. Once I upgraded the RAM to 192 MB (the max), I was able to use Debian 4 (later 5) and Openbox/LXDE. If it's possible to find some more RAM for that somewhere, you'd have many more options.

---

