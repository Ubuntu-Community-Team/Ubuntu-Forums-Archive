---
title: "Portable Apps"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by kf4tqj on 2007-10-07
With Windows, I could put portable versions of Firefox, Thunderbird, Gaim and others on a thumb drive. Then I'd always have my apps with me no matter what computer I'm on. I can't get these to work with Ubuntu yet. 
Is there any way to do this where the thumb drive can go from one Ubuntu box to another? Also, any way to work it cross platform?
I found nothing for Linux at [www.portableapps.com](www.portableapps.com)
Thanks
Woody

---

### Post by williamwade on 2007-10-07
You could try wine.

I'm assuming you know what wine is

---

### Post by anemptygun on 2007-10-07
According to this blog you cannot use portable apps natively on linux... but... you may be able to get them to work under wine.

[http://www.linuxfortravelers.com/general/portable-apps](http://www.linuxfortravelers.com/general/portable-apps)

---

### Post by funrider on 2007-10-07
you can actually build a portable OS with a flash drive. Try searching "live cd on flash drive" to learn more.

---

### Post by n3tfury on 2007-10-07
> **funrider said:**
> you can actually build a portable OS with a flash drive. Try searching "live cd on flash drive" to learn more.

yeah, but that would suck to have to boot into another OS to use one app.

---

### Post by om1 on 2007-10-07
ok i tried running portable firefox in wine and it worked...
to install wine just open up add/remove and search for it .... then you can just open the exe just like in windows

---

### Post by kevdog on 2007-10-07
Id just put damn small linux or puppy linux on a USB stick and run that -- that would assume however you could boot from the USB drive -- which would assume that the boot order is set correctly or that you have access to the BIOS to change the settings.

---

### Post by n3tfury on 2007-10-07
> **kevdog said:**
> Id just put damn small linux or puppy linux on a USB stick and run that -- that would assume however you could boot from the USB drive -- which would assume that the boot order is set correctly or that you have access to the BIOS to change the settings.

again, a royal pain in the butt if there's an OS already running.

---

### Post by kf4tqj on 2007-10-07
Thanks, I'm downloading Wine now. ( may be a while, I'm on Dial-Up.)
Is there any trick to running it or is it self explanitory?

---

### Post by om1 on 2007-10-07
if your installing from add/remove... no problem after it installs you should just be able to click on the exe and thats it.... otherwise you probably will have to configure wine..... either way you shouldn't have much of any problems.... only time you will is if you are trying to run games under wine

---

### Post by kevdog on 2007-10-07
Wine -- yea it works sometimes, but seriously its a pain in the butt and apps often run slower inside of wine.  A partial but not very elegant solution.

---

### Post by anemptygun on 2007-10-08
Let us know how that works out!:KS

---

### Post by anaconda on 2007-10-08
after you have installed wine you will need to run (in terminal):
```
winecfg
```
and just select OK
that will create the .wine folder to your home directory. It is needed for running wine.

I have had good experiences with portableapps.. eg. portable photoshop CS2

---

### Post by nooby on 2007-10-08
Maybe this experiences  is of help too?  
[http://www.linux.com/articles/54920]("http://www.linux.com/articles/54920")

> Wine Doors opens Windows under Linux
By Nathan Willis on June 13, 2006 (8:00:00 AM)

When I first used Wine to try to install Windows software on my Linux machine, I found it less than user-friendly. Fortunately there was an application called WineTools to help smooth out the process. WineTools helps you download essential Windows add-ons like DLLs and Internet Explorer -- a necessity for most users, since a great many third-party Windows apps rely on IE's low-level system integrating to implement essential services. 

But WineTools has not aged well, and using it increasingly causes problems for other Wine applications. Luckily a new project called Wine Doors is picking up where WineTools left off.

Like WineTools, Wine Doors is designed to user-friendlify your Wine installation -- setting up phony Windows drives, adding Windows applications, and so on. 

The goal is to let users manage their Wine-based apps with point-and-click ease -- from free apps such as Google Earth to closed, commercial software like Photoshop or Internet Explorer -- as well as support packages like font packs supplied by Microsoft.

i neveer used wine but it could maybe allow you to do what you want?

---

