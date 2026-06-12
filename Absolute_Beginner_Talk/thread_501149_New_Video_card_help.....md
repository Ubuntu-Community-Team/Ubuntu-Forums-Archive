---
title: "New Video card help...."
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Teddy_P on 2007-07-14
I am planing on getting a new video card. The computer is a:
Compaq evo
D5M/P1.8/20/p/256c/6 US
So I am guessing 1.8 Mhz
256 ram

I am running Edubuntu, Kubuntu, and Ubuntu Fiesty.
I want to try compiz.
I have a thread going over there but wanted to make sure it would work with Ubuntu also, beings its more important than compiz. [[COLOR="Red"]link to thread[/COLOR]]("http://forum.compiz.org/viewtopic.php?p=9893#9893")

I have been looking at this one all day:
[[COLOR="Red"]link to video card[/COLOR]]("http://forum.compiz.org/viewtopic.php?p=9893#9893")

Found this [[COLOR="Red"]Document Page[/COLOR]]("http://doc.gwos.org/index.php/Nvidia/Geforce6")

XFX PV-T44A-WAN 
Card model   6200 256 Mb DDR TV DVI 
   Functionality 2D   Works out of the box 
   Functionality 3D   Works out of the box 
   Issues    Require Nvidia-glx-Package for 3D Functions. Install it here Install_Nvidia_driver

But am still unsure if its what I want or need.

Also on the mother board it says 1.5V AGP cards only. I called Tiger Direct and the lady who answered said all AGP cards are 1.5V

So what do you think?
Should I get it or not?



Thanks
Teddy

---

### Post by Vajra Vrtti on 2007-07-15
> I want to try compiz.
> Card model 6200 256 Mb DDR TV DVI
I have a nVidia 6200 and its 3D works fine, but I use Beryl.
All I had to do was to install the packages: 
[B][LIST]
[*]nvidia-glx 
[*]beryl 
[*]beryl-manager 
[*]emerald-themes
[/LIST][/B]Is you current card also nVidia?

---

### Post by w4ett on 2007-07-15
I just ordered the 6200 card Yesterday!....Looks like a GREAT budget card...I'm looking forward to getting it running.

---

### Post by Teddy_P on 2007-07-15
> **Vajra Vrtti said:**
> I have a nVidia 6200 and its 3D works fine, but I use Beryl.
All I had to do was to install the packages: 
[B][LIST]
[*]nvidia-glx 
[*]beryl 
[*]beryl-manager 
[*]emerald-themes
[/LIST][/B]Is you current card also nVidia?

Yes the card I have now is nVidia Vanta.
When I do a search for the card I want I see 128 MB.
Did they change or am I not looking at the right stuff.


Teddy

---

### Post by Teddy_P on 2007-07-15
I was also looking at compiz because won't they or haven't they all ready merged?

Teddy

---

### Post by Teddy_P on 2007-07-15
This card: Is a GeForce 6200
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1776106&CatId=933]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1776106&CatId=933")

And this one is a GeForce 6200 LE
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2190054&CatId=933]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2190054&CatId=933")


I don't know which one to order?
Where did you get yours from?



Thanks
Teddy

---

### Post by Vajra Vrtti on 2007-07-15
> Yes the card I have now is nVidia Vanta.
So I think you will have no problem booting with the new card. Anyway, make a safe copy of *etc/X11/xorg.conf* before you install it.

> I was also looking at compiz because won't they or haven't they all ready merged?
They merged into Compiz Fusion, but they are not in Ubuntu repositories yet. Beryl is much easier to install (just the packages I listed above) and you will have enough fun. It works fine for me. Ubuntu 7.10 will probably have Compiz Fusion.

My video card is that XFX one. I bought it in my country.

---

