---
title: "turn off monitor"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by pspcz on 2007-07-20
hello,

I installed 7.0.4 server on an older flat panel imac and would like to turn of the display as it is only used as a server, any suggestions?

i have tried xset but am getting this error 

xset:  unable to open display ""

thanx in advance


Pz

---

### Post by kngunn on 2007-07-20
Have you thought about setting the screen to shut off quickly in your Power Management Preferences?  Tell it to sleep the display after 11 minutes (I think that's the minimum) and forget about it.

---

### Post by jellisii on 2007-10-17
pspcz:  it sounds like you may be attempting to issue the xset command from a terminal that is not attached to the x windows session that you are trying to control.  Unless I am mistaken, xset will need to be issued from inside the x session you are trying to alter.

That being said, I am having a similar problem.  

I am using a 15" flatscreen Imac g4 with 7.04.

The problem appears to be that the x.org server doesn't know how to properly suspend this monitor.  When I issue "xset dpms force off " or "xset dpms force standby", I get the same result:  the LCD panel looks like it half stops working, leaving large red sections still on, with the backlight not appearing to dim at all.  

This isn't a deal breaker, but I have the machine acting as  a web server, like pspcz.  I'd rather not cook the backlight when I'm not using it locally.  Right now I'm just using a blank screen so the light isn't too bright pouring out of my office at night.

Thanks in advance.

Edit 1:  Same problem with 7.10.

---

### Post by aurenus on 2007-11-04
> **pspcz said:**
> hello,

I installed 7.0.4 server on an older flat panel imac and would like to turn of the display as it is only used as a server, any suggestions?

i have tried xset but am getting this error 

xset:  unable to open display ""

thanx in advance


Pz

Hi pspcz

Did you ever find a solution to this?  I have the exact same thing as you - I have a laptop running ubuntu server and I want to turn off the laptop lcd since I log in remotely to it.

Cheers

---

### Post by bleedingpowers on 2008-07-13
Hey, guys.

Did any of you find a solution to turn off the display on a ppc imac? I'm currently using ubuntu server 8.04 with xubuntu as a desktop manager. Everything else works (it even suspends properly). I just can't seem to find an answer to shut just the screen off. I've been looking around for an answer, but no luck yet.

If I try something like:
```
xset dpms force off
```
the screen goes orange.

Any other ideas? I have tried all the other xset dpms options without luck.

---

