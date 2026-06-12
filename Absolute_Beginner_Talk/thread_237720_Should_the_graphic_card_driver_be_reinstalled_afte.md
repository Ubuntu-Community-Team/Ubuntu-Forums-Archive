---
title: "Should the graphic card driver be reinstalled after changing resolution?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by SkippyJames on 2006-08-16
Hey, 

I've bugged the community too much these days about the resolution issues,but this is probably the last question after that i am giving up the fonts. 

I've changed my resolution from 1024x768 to 1280x800 and now my fonts looks bad somehow, i switched on auto-hinting and smooth font from dpkg-reconfigure fontconfig but that was a very small improvement. now i was thinking maybe i should reinstall the nividia drivers after the resolution change maybe that will fix it. 

(asus a6jc widescreen, intel 945 chipset and nividia 7300 go) if it helps.

Appreciate any help 
thanks

---

### Post by mrazster on 2006-08-16
I don't have real solution for you...but I do know that you don't have to reinstall the drives after resolution change. That's not the problem.

However one thing comes to mind...are you really sure 1280x800 is the native resolution for your monitor/panel ..?

I have a 24" widescreen with 1920x1200 as native res but when I change it so something else...doesn't matter what, my fonts get really uggly...hence my question to you.

---

### Post by SkippyJames on 2006-08-16
I am not really sure but in [www.asus.com](www.asus.com) when i check the specs out for the display it says something like this:
Display
	
15.1" XGA/SXGA+ & 15.4" WXGA (1280*800) / WSXGA+ (1680*1050)
Video Graphics & Memory
	
NVidia™ GeForce™ Go7300 128MB

i am not sure what those means. But i figured it supports 1280x800 and 1680x1050.

---

### Post by ComplexNumber on 2006-08-16
> Should the graphic card driver be reinstalled after changing resolution? the answer to that is "no". you can change the resolution as many times as you have energy for without reinstalling. its usually best to log out and then back in again for the full changes, though. well, i do anyway.

---

### Post by mrazster on 2006-08-16
> **SkippyJames said:**
> I am not sure what those means. But i figured it supports 1280x800 and 1680x1050.

well..mabye you ought to try 1680x1050 then...and se if it supports it...I'll bet my last cent that you got your problem there.

*EDIT:* I had a look at it on asus site for ya...and I'm pretty sure 1680x1050 is the resolution for you.

---

### Post by tseliot on 2006-08-16
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

