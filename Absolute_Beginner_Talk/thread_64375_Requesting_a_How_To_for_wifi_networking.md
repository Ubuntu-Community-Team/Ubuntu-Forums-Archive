---
title: "Requesting a How To: for wifi networking"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by JonnyB on 2005-09-10
I know that someone must have wrote something on how to set up a wireless network but I did some minor searching on how to set up a wireless network on Ubuntu and didn't find anything. So if someone can point me in the right direction that would be helpful.

I have a Belkin Pre-N router and Wifi Card. I want to be able to connect to my network/internet just like I would in Windows.

Thanks

---

### Post by John.Michael.Kane on 2005-09-10
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)


And welcome to Ubuntu/gnu/linux

---

### Post by JonnyB on 2005-09-10
oh cool. Thanks dude. So which download would i need for Ubuntu? Is ubuntu debian?

---

### Post by John.Michael.Kane on 2005-09-10
ndiswrapper you can use your windows drivers with it.

you may want to searh here since it is for networking problems
[http://ubuntuforums.org/forumdisplay.php?f=62](http://ubuntuforums.org/forumdisplay.php?f=62)

---

### Post by daller on 2005-09-12
The only thing needed, is the .inf-file?

---

### Post by cbudden on 2005-09-12
[QUOTE=daller]The only thing needed, is the .inf-file?[/QUOTE]
 Yes, for NIDS wrapper to use.

---

### Post by Seer on 2005-09-12
WRONG!!!!!!!

Nothing, not Ubuntu, Not Any other Distro, Not NDIS Wrapper NOTHING supports belkin pre-n nics.

Believe me I spent weeks on it with no other assistance other than the usual wise ass remarks about daring to use something not in a 10 year old laptop.

My last set of posts which got 0 response are here [http://www.ubuntuforums.org/showthread.php?t=43511](http://www.ubuntuforums.org/showthread.php?t=43511)

I sent everything I had and drivers and a NIC to the NDISWrapper team

nada

Buy a new NIC and it might work with the router ... welcome to the joys of Linux hardware support  \\:D/

---

### Post by poofyhairguy on 2005-09-12
[QUOTE=Seer]WRONG!!!!!!!

Nothing, not Ubuntu, Not Any other Distro, Not NDIS Wrapper NOTHING supports belkin pre-n nics.
[/QUOTE]

If that is the case, this might be the only option:

[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

Try the demo.

---

### Post by Seer on 2005-09-12
Been there, done that... gives exact same issues (plus costs money!)

---

### Post by atrus325 on 2005-09-12
What chipset do these cards use?  There are other options than Ndiswrapper depending on chipset.

> The only thing needed, is the .inf-file?

Some drivers need an accompanying .sys file as well.

J.

---

### Post by Seer on 2005-09-13
[QUOTE=atrus325]What chipset do these cards use?  There are other options than Ndiswrapper depending on chipset.



Some drivers need an accompanying .sys file as well.

J.[/QUOTE]
 I forget the chipset (I'm at work atm and will check later) but the sys and bin files all get pulled in but with no joy

---

