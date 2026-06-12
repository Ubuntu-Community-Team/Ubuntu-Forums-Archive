---
title: "I'm curious about PCBSD"
date: 2007-04-01
forum: BSD
---

### Post by Peter Mount on 2007-04-01
Hello

I've read conflicting articles linked on Distrowatch about the latest PCBSD and from what I understand they have different comments to make about driver support. At least that's what I remember :-)

How would PCBSD compare to (K)Ubuntu in terms of:

1 Driver support
2 Getting flash to run
3 Getting IES4Linux to work on it
4 Using Firefox, Lynx, Opera and Konqueror
5 Installing an older version of LAMP ie. php4.x and MYSQL 4.x as well as Apache
6 Connecting to cable internet
7 Using KDE

All this seems pretty straight forward in Kubuntu (apart from my parrallel Canon scanner that I haven't bothered with anyway).

I've currently got a Pentium 2-350 with 448mb of PC100 SDRAM and I'm looking at buying an Intel Mac later this year.

I'm quite happy using Kubuntu but I thought as I've got 2 hard drives it might be fun to try something different on my other hard drive if I have the time

Thanks

---

### Post by raqball on 2007-04-01
Dont bother! I just gave it a shot yesterday... Same ol same ol... It's NOT ready.... No wireless, no sound and no mouse after boot.... I did get it all working but it's a pain and a waste.... Just me 2 cents worth since i was warned by a mod the last time I posted about BSD not being ready...... :rolleyes:

---

### Post by Peter Mount on 2007-04-01
> **raqball said:**
> Dont bother! I just gave it a shot yesterday... Same ol same ol... It's NOT ready.... No wireless, no sound and no mouse after boot.... I did get it all working but it's a pain and a waste.... Just me 2 cents worth since i was warned by a mod the last time I posted about BSD not being ready...... :rolleyes:

OK. I'll take your word for it. I'll just stick with Kubuntu as I know it works :-)

---

### Post by hanzomon4 on 2007-04-02
PC-BSD is neat, I installed it on a usb hard drive and it detected all of my hardware accept my usb mouse(which was fixed by using a usb to mouse-port(?) converter and sound card(fixed by installing oss v4). It's fast and the ports system is great, pbi's are to. If you have a spare hard drive or partition you should give it a try. It's the ubuntu of the BSD world but it's not (K)ubuntu. 

List of have nots
[list][*]Automounting usbdrives, ipods, and such[*]Not as many drivers for stuff like wireless cards[*]Flash is stuck at v7[*]Cant read linux file system and vice versa[/list]

List of haves
[list][*]Linux compatibility layer(you can install linux firefox and flash 9) ;)[*]GUI installer[*]One click install via .pbi[*]Easy src install via ports tree[/list]

Bottom line, if you have the space you should try it....

---

### Post by Peter Mount on 2007-04-02
> **hanzomon4 said:**
> 
Bottom line, if you have the space you should try it....

Well if I find I have the time to try something different I'll give it a whirl on my other hard drive.  I just need to take care of other things first

Have fun

---

### Post by handy on 2007-04-03
Like anything non-windows, you have to take your chances re. your hardware...

Or research thorougly.

---

### Post by xx75 on 2007-04-03
> **hanzomon4 said:**
> 

List of have nots
[list][*]Automounting usbdrives, ipods, and such[*]Not as many drivers for stuff like wireless cards[*]Flash is stuck at v7[*]Cant read linux file system and vice versa[/list]

I had no trouble with  usb drive automounting (LG 1gb), may be just lucky?

You can read your linux filesystem, just have to make a mount point. I use it to get all my mp3's on Ubuntu to Amarok on PC-BSD.

> List of haves
[list][*]Linux compatibility layer(you can install linux firefox and flash 9) ;)[*]GUI installer[*]One click install via .pbi[*]Easy src install via ports tree[/list]



PBI's are pretty crappy (personal opinion). Easy to install but usually out dated. Launch icons don't intergrate well with the K menu, just thrown under the PBI Files heading. Though PC-BSD docs encourage you to use them, as they are unique to PC-BSD, I prefer ports.


I have had trouble with my printer (HP C6100) on PC-BSD:(  not an issue with Ubuntu:) 

> Bottom line, if you have the space you should try it....

Absolutely. Only one way to find out! The GUI installer is a no brainer.

Have fun.
xx75

---

### Post by handy on 2007-04-03
The newest version of PBI maker software installs the software on the menu appropriately now I believe.

---

### Post by mips on 2007-04-04
> **handy said:**
> The newest version of PBI maker software installs the software on the menu appropriately now I believe.

Yes. It's very much dependant on which version of pbi maker software was use to create the pbi with.

---

### Post by hanzomon4 on 2007-04-05
> **xx75 said:**
> I had no trouble with  usb drive automounting (LG 1gb), may be just lucky?

You can read your linux filesystem, just have to make a mount point. I use it to get all my mp3's on Ubuntu to Amarok on PC-BSD.





PBI's are pretty crappy (personal opinion). Easy to install but usually out dated. Launch icons don't intergrate well with the K menu, just thrown under the PBI Files heading. Though PC-BSD docs encourage you to use them, as they are unique to PC-BSD, I prefer ports.


I have had trouble with my printer (HP C6100) on PC-BSD:(  not an issue with Ubuntu:) 



Absolutely. Only one way to find out! The GUI installer is a no brainer.

Have fun.
xx75

Note: it can't read jfs or xfs file systems, I don't use ext3....... my bad

---

### Post by Thulemanden on 2007-04-22
> **Peter Mount said:**
> 
I'm quite happy using Kubuntu but I thought as I've got 2 hard drives it might be fun to try something different on my other hard drive if I have the time


It doesn't easily dual boot; you'll have to manually work on it.

It has some WMV file support.

It's very safe and stable.

It's all KDE so you can't say it's the Ubuntu of BSD. It's nonsense,

I can recommend it as a stand alone not dualbooting.

---

