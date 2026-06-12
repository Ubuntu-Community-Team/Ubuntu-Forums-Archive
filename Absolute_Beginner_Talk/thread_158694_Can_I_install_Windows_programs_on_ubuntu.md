---
title: "Can I install Windows programs on ubuntu?"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by polishemokid on 2006-04-11
I am fairly new to linux, its pretty awesome so far.  Im a winxp and mac oc tiger user.  I built a machine the other day for the heck of it and installed ubuntu on it.  
I am wondering how can i run a windows based program on it, if it is indeed possible at all.  i.e. Games, Photoshop etc.  That I have for windows.

---

### Post by daWabbit on 2006-04-11
The snap answer is no, though you can use things like wine, Crossover Office and such to run them in emulation. Plus, there are various virtualization schemes to try, such as Xen. Generally, the performance hit from running things in emulation is too high for my tastes. That said, there are a LOT of folks doing it happily.

A bit of reading will probably satisfy your curiosity. My own solution is to keep a Win XP machine here, just in case. It sits there running seti@home and doesn't get used because I don't game and everything I need is available in Linux. 

Jack

---

### Post by nalmeth on 2006-04-11
Yes these things *can* be run in linux, but you have to aquire the compatibility layers to use different windows apps.
A free, general windows compatibility layer is available called wine, but is limited due to legal problems and stuff.
Cedega is a company that makes most windows games (including hard 3D games) work on linux. They charge a minimum total of $15, that's $5 a month for minimum 3 months during which you get all the updates. After the 3 months are up, you can still play with cedega, but won't get the updates. Cedega is a project that forked wine specifically for gaming.
Crossover Office is a product that will let you use some of the major windows app on linux such as Photoshop, Microsoft Office, and so on.
I believe it costs upwards of $70 dollars! yikes!
cxoffice is also a fork of wine.
Unless you depend on photoshop, you may find the Gimp to be quite suitable for what you need. The GimpShop is a different packaging of the Gimp, meant to be similar to photoshop. Gimp is totally free.
Check this site for some windows equivalent apps in linux:
[http://doc.gwos.org/index.php/AppHelper](http://doc.gwos.org/index.php/AppHelper)

---

### Post by aysiu on 2006-04-11
Your best bets are, in this order:

1. Finding a native Linux equivalent
2. Wine
3. Cedega
4. Crossover Office

---

### Post by wolfee on 2006-04-11
some of them. Wine is not an emulatore but it will allow you to run some programs from microshaft here are some links to get you started. 1st install Automatix then run it from system tools and install wine.Any program you download make sure it is compatible with franks corner list before installing it. also you will have to do tricks on some programs to get them to run in wine. also in your home folder where wine should be installed hit viewthen click on show hidden files this will show .wine which is where all your programs reside. Here are the links
For Automatix:
[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405) 
 For lists of what programs work under wine:
[http://frankscorner.org/](http://frankscorner.org/)

Enjoy!!!

---

### Post by AndrewCaul on 2006-04-11
[QUOTE=aysiu]Your best bets are, in this order:

1. Finding a native Linux equivalent
2. Wine
3. Cedega
4. Crossover Office[/QUOTE]
And if that fails:
5. Dual boot.

---

