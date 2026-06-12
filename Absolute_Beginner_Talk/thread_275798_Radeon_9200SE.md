---
title: "Radeon 9200SE"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2006-10-11
I have a Radeon 9200SE in my computer. In an effort to make it run better graphics I seem to have made it somewhat worse and now I can't get it back. When ubuntu first was installed the graphics weren't half bad, but I tried to get 3D acceleration to work. In an effort to do that I installed the drivers using the explaination I found in the WIKI, but it seems to have gotten worse and I believe it's because things need to be tweaked. 

I am just wondering if anyone knows for an online step by step for setting up this card.

Thanks!;)

---

### Post by podunk on 2006-10-11
I used this page for my 9200 and it boosted my glxgeears up above 800:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Method 1 works for us. Be sure to follow it all the way to the end!

---

### Post by s4050058 on 2006-10-16
> **Bigguy2468 said:**
> I have a Radeon 9200SE in my computer. In an effort to make it run better graphics I seem to have made it somewhat worse and now I can't get it back. When ubuntu first was installed the graphics weren't half bad, but I tried to get 3D acceleration to work. In an effort to do that I installed the drivers using the explaination I found in the WIKI, but it seems to have gotten worse and I believe it's because things need to be tweaked. 

I am just wondering if anyone knows for an online step by step for setting up this card.

Thanks!;)

Warmest greetings, I have a Radeon 9200SE and my glxgears fps is 1021.
Some points to remember:
ATI fglrx - unfortunately poor in performance.[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
ati/radeon DRI drivers - consistently good [http://ubuntuforums.org/images/smilies/icon_mrgreen.gif](http://ubuntuforums.org/images/smilies/icon_mrgreen.gif)
Now if you have really rogered your setup, from a terminal you can run
sudu dpkg-reconfigure xserver-xorg and pick ati in the graphics driver section and all should  be well. 
enabling AGP fast write seems to stuff things completely - I don't recommend it 
Now seeing as we have the same card, you should be able to get my performance by using my config: although your BusID may be different:
you can use lspci -x to confirm your busID

Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"AGPMode"	"4"
	Option		"EnablePageFlip"	"true"
EndSection

I should think that would work for you.  The last two options are essential for good performance.
Good luck with it.

---

### Post by Bartender on 2006-10-16
I just pulled my 9200SE and plugged in a comparable NVidia card.  Problems went away.

---

### Post by blackpaw on 2006-11-12
> I just pulled my 9200SE and plugged in a comparable NVidia card. Problems went away.
Although I despise solving problems like this, I might just do that aswell..
I've been trying now for weeks to get a useable mythtv box running with my old 9200se and this card is just a huge pain in the you-know-where...

Any recommendations on fan-less nvidia cards that perform nice with edgy/mythtv? ;)

cheers

---

