---
title: "My problems with making the jump to linux."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Redorb1790 on 2008-03-18
So I made the jump a couple of days ago and I've already had to reinstall Ubuntu 3 times from various crashes that are unknown to me of why they happened. I've fixed most of the issues but there is still one small annoyance. When I got to look at the size of a folder by right click properties it crashes the desktop and reloads it but the thing is its only when I look at the size of folders. Anything else is just grand when I look at them. Help would be much appreciated.
Mateo

P.S. Linux killed my ipod I won't go into the details how but it uploaded random crap to it and filled up its hard drive thus rebooting it made it freeze at the screen.

My ipod is now laying on the kitchen counter with the internals stripped out.
*sigh*

---

### Post by PmDematagoda on 2008-03-18
What are the specifications of your PC, also what release of Ubuntu are you trying to install?

---

### Post by Redorb1790 on 2008-03-18
7.10-Version of Ubuntu
3.2 Ghz Pentium 4 with HT
1.5 Gigs of Ram
ATI PCI Express X300
Onboard Soundcard
Not sure on the motherboard

---

### Post by TenPlus1 on 2008-03-18
Did you Unmount your iPod before removing it from the USB port ???

---

### Post by Tomatz on 2008-03-18
> **TenPlus1 said:**
> Did you Unmount your iPod before removing it from the USB port ???

That would be the problem i reckon.

---

### Post by Tomatz on 2008-03-18
As for the "properties" bug this is a well reported bug a link to the fix is below.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=449070](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=449070)


Just open synaptic 

click search  

search for   nautilus

r-click on nautilus

click upgrade

Any probs (or if you can't upgrade) post back :)

---

### Post by Boyohazard on 2008-03-18
Probably too late but if your iPod crashes/freezes you can hold the select button and the menu key down for about 5 seconds to reset it.

Probably also too late but don't use an iPod :biggrin:

---

### Post by Sef on 2008-03-18
> Did you Unmount your iPod before removing it from the USB port ???

To unmount a device like an ipod, usb key, flash drive, or other similar device, simply right click on the icon and go down to unmount.   When you unmount, you shut that device off.  If you fail to unmount, you could end up damaging the device or corrupting some files.

---

### Post by Redorb1790 on 2008-03-18
The upgrade was grayed out =/

---

### Post by Tomatz on 2008-03-18
Can you give me the version number of the nautilus package you are currently using?

It should be nautilus1:2.20.0-0ubuntu7

Maby upgrading to nautilus1:2.20.0-0ubuntu7.1 might fix the bug.

 I have inserted a link to this (nautilus updatd) below:

[http://packages.ubuntu.com/gutsy-updates/nautilus](http://packages.ubuntu.com/gutsy-updates/nautilus)

Just scroll down to the bottom of the page and choose the relevant architecture for your computer (i386).

---

### Post by Redorb1790 on 2008-03-18
2.20.00

---

### Post by Tomatz on 2008-03-18
cool 

Maby upgrading to nautilus1:2.20.0-0ubuntu7.1 might fix the bug.

I have inserted a link to this (nautilus updated package) below:

[http://packages.ubuntu.com/gutsy-updates/nautilus](http://packages.ubuntu.com/gutsy-updates/nautilus)

Just scroll down to the bottom of the page and choose the relevant architecture for your computer (i386). 
Download then double click it to install.

---

### Post by Redorb1790 on 2008-03-19
Alright thanks I just have one other question with linux. When it comes to emulating games with wine, cedega, and crossover which would be the best option without pricing in mind.

---

### Post by undertakingyou on 2008-03-19
> **Redorb1790 said:**
> Alright thanks I just have one other question with linux. When it comes to emulating games with wine, cedega, and crossover which would be the best option without pricing in mind.

I have used Wine to play Half Life, and Warcraft.  It also runs other things very nicely like uTorrent.  Haven't tried the others, but you're not out any if you try wine  :)

---

### Post by Redorb1790 on 2008-03-19
I installed guild wars under wine this morning before I left for school so I'm hoping it works without issues. I have a feeling Im going to have to do something odd with it though.
*sigh*

---

### Post by Tomatz on 2008-03-19
If the game uses directX then use cedega.

If the game uses openGL then use wine.

*But if you want my advice i hate to say it but if the game does not run on linux Nativly just use windows.*

[U]A few games (fps) that run on linux nativly:
[/U]
et quake wars (my personal favorite)

wolfenstien et (and all mods)

doom 3

quake 4

urban terror

quake 3

open arena

unreal tournament

world of padman  

Someone else will no doubt add more :)

---

### Post by Redorb1790 on 2008-03-19
Ok well my dad sent me our Windows XP disk in a .img attachment because he's in chicago atm with all our computer stuff. Any who I was wondering if there was anyway to burn a .img file in linux or convert it into another format such as .iso so I can make a cd out of it and dual boot linux and windows.

---

### Post by bro on 2008-03-19
Don't know about your problems with ubuntu. Ipods however can might be recovered by following [ instructions from apples site. ]("http://www.apple.com/search/support/?q=firmware+ipod+restore")

---

### Post by Tomatz on 2008-03-19
> **Redorb1790 said:**
> Ok well my dad sent me our Windows XP disk in a .img attachment because he's in chicago atm with all our computer stuff. Any who I was wondering if there was anyway to burn a .img file in linux or convert it into another format such as .iso so I can make a cd out of it and dual boot linux and windows.


Yeah its called acetone iso :)

Get it here:

[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

---

### Post by uthturn on 2008-03-19
remember if you install windows it will install it's mbr you will have to reinstall the boot loader

---

