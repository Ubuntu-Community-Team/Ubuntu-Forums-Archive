---
title: "Wanting to convert to Linux..."
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by achafe on 2005-12-18
So I've decided that linux is for me and want to convert from Windows98, to Ubuntu!!  Over months, I've read lots of 'is it right for you' articles and have come to the conclusion that I will try to install Ubuntu on my pc.

Problem is my pc, 200Mhz, MMX, 64megs of RAM and 4.3Gb hdd.  I connect to the internet through a wireless linksys **USB** network adapter.  I have read about lite installs and am pretty confident I can manage, but I'm not sure what desktop I should use (I really love the gnome style).

I would need a messaging program (Gaim?), a browser, mediaplayer, and an office program.  I'm afraid this to much to ask with my limited resources.

Also, the installer fails to pick up internet connection with the USB adapter...is this a problem?

Anyway, I'm wondering if my hardware will prevent me from using linux (even though I'm very in love with ubuntu...lol!), and any advice would be very much appreciated!  I know you guys are an excellent community!

Cheers!

---

### Post by arctic on 2005-12-18
Hmm... I would try "Damn Small Linux" first, before heading into Ubuntu with that computer.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Good hardware detection, nice and lightweight Fluxbox window manager, can be used as live-cd and install-source and can use the whole debian package mirrors with lightweight office solutions like e.g. Abiword. And it's only 50MB! :D

---

### Post by kairu0 on 2005-12-18
For a system of those specifications, Gnome is out of the question. You should look into icewm, fluxbox, or fvwm.

For your office needs, you would want to use Abiword instead of OpenOffice.

For your Internet browsing, perhaps the Epiphany browser. FireFox would be very sluggish.

Please check if your network adapter is listed on this page:

[http://www.qbik.ch/usb/devices/search_res.php?pattern=wusb54g](http://www.qbik.ch/usb/devices/search_res.php?pattern=wusb54g).

If you have a different model, please state it.


P.S. Damn Small Linux would be a REALLY good idea, too. You might want to look into that first.

---

### Post by dickohead on 2005-12-18
While some versions of Linux will run on specs like that, they won't be pretty, mostly command based, or running something less resource intensive like iceWM. I run Ubuntu on a couple of servers, my lowest specs server is running dual Pentium 200's with 360mb of memory, and it's painfully slow (especially when compared to my AMD 3200 XP, 1gb Dual channel 3200, desktop). My other server however, has a 700Mhz Pentium 3 in it, with 512MB ram, and it runs very well.

So you will more than likely need to upgrade at the very least your memory, i'd go for around 256mb.

---

### Post by fuscia on 2005-12-18
fluxbox is pretty light and is very useable. 
i had trouble with the server install, but i really didn't know what i was doing. 
my linksys usb adapter worked out of the box, but it's an older 802.11b (it's perfectly fine).

---

### Post by achafe on 2005-12-18
Wow. What quick replies, you guys are great!

I actually have been given a cd with DSL on it, but when I booted it I couldn't get internet connection that wasn't dialup, so I haven't really given it a real chance yet, as my heart was set on Ubuntu, hahaha!

But I'll dig through my cd's and give it a spin.

My network adapter is a linksys WUSB11 If it could work in DSL I'd be very happy.

Also, does DSL have a instant messenger?

Thanks for the help guys!

---

### Post by stuporglue on 2005-12-18
Check out Xubuntu. It's Ubuntu with the XFCE ([http://www.xfce.org/](http://www.xfce.org/))

I install Xubuntu on PI and PIIs all the time for a computer recycling program I run ([http://stuporglue.org)](http://stuporglue.org)). It works pretty well. 

I throw on Abiword, Gnumeric, Gaim and Xpdf. 

Here's the instructions for installing Xubuntu. Since you're not on BYU campus, adding the physics mirror won't help you much. 

[http://stuporglue.org/lowmem.php](http://stuporglue.org/lowmem.php)

---

### Post by achafe on 2005-12-18
And could I install the Xubuntu without internet connection?

---

### Post by stuporglue on 2005-12-18
Technically yes, but it would be a lot of work. You'd have to manually download the xubuntu package and all it's dependencies. This would probably be more work than it's worth. 

You can do the server install from the Ubuntu install CD, and if Ubuntu supports your wireless card out of the box, the server install would be enough to get your net connection up.

---

### Post by achafe on 2005-12-18
The problem is, the installer won't pick up my usb network adapter as an interent connection.  Is the information for xubuntu on the 5.10 install cd?

I think I'll try to get it working in DSL, although if that xfce wouldn't slow my pc to much, I'd really like to try it.

Thanks for all you help!

---

### Post by stuporglue on 2005-12-18
> The problem is, the installer won't pick up my usb network adapter as an interent connection. Is the information for xubuntu on the 5.10 install cd?


It's not, you have to enable some network repositories to get the Xubuntu info. 

You'll like DSL. It's very fast, and a good system. 

If you have access to a fast connection with a CD burner, you could also download the full Debian CD set. It's like 7 CDs, but you'd never need a net connection to install anything. I downloaded the set for my brother since he's on dialup, and it's worked pretty well. 

Ubuntu and DSL are based on Debian, and almost any program you would ever want is available on the CDs including Xfce and Fluxbox.

If you go the Debian route you'd want for example the CDs ending in 30r5-i386-binary-*.iso

Here's a mirror, but there's probably one closer to you. 
[http://debian.midco.net/pub/iso/](http://debian.midco.net/pub/iso/)

---

### Post by Evil Whisper on 2005-12-18
You also may want to check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=103806&highlight=Oubuntu](http://www.ubuntuforums.org/showthread.php?t=103806&highlight=Oubuntu)

I think you may be able to run ubuntu with openbox :-)

---

