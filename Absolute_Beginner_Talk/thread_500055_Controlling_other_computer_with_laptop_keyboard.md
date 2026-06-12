---
title: "Controlling other computer with laptop keyboard"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-07-13
Heres the deal. I'm getting a new laptop. I can't decide whether or not to spend 20 more bucks on bluetooth. Because its a thinkpad, there is no other input device I could ever want to use on it.

EXCEPT: in the case that lenovo comes out with a bluetooth version of an external thinkpad keyboard with trackpoint. Which might happen.


But anyways.. I might want to control my MACbook with the thinkpad keyboard built into my laptop. Is there a way to do this. Would it require both having bluetooth.

---

### Post by Nekiruhs on 2007-07-13
> **systemintheglitch said:**
> Heres the deal. I'm getting a new laptop. I can't decide whether or not to spend 20 more bucks on bluetooth. Because its a thinkpad, there is no other input device I could ever want to use on it.

EXCEPT: in the case that lenovo comes out with a bluetooth version of an external thinkpad keyboard with trackpoint. Which might happen.


But anyways.. I might want to control my MACbook with the thinkpad keyboard built into my laptop. Is there a way to do this. Would it require both having bluetooth.
You could do SSH into the mac and you would control the mabook with your Lenovo laptop.

---

### Post by zanglang on 2007-07-13
You could configure Synergy on both of them, with your Thinkpad as server and Mac as client. The software is available on the repositories as 'synergy', and there's a GUI 'quicksynergy' as well.
[http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)

Or, since it's unlikely that you'll be using both laptops at the same time a lot, just setup VNC on the Macbook so you can view and control its desktop from your Thinkpad when you need to.

---

### Post by systemintheglitch on 2007-07-13
It seems like all of these solutions (allthough cool) will have some sort of preformance downfall or require an internet connection. 

Is there a way to do this without an internet connection with good preformance? Shouldn't there be a program that takes my keyboard input on my thinkpad, transmits my keyboard strokes/mouse movement across the bluetooth? and then my mac just sees it as an external keyboard?

thanks everyone for the help.

---

### Post by systemintheglitch on 2007-07-13
Like i aluded to..

It looks like synergy requires that you link your computers over a network.

Now.. Is there a way to network two computers (one windows, one mac/linux) over a "bluetooth network" .. I wouldn't know, because i know nothing about networks.. But this would give me the internet/cableless networking i so desire!

---

### Post by sundy58 on 2007-08-05
I just got Quicksynergy configured with my XP box.

Ubuntu is the server Xp is the client.

I put the **_name_** of the XP box in the Quicksynergy server.

I put the **_IP adress_** in the XP client configuration.

It did not work for me in any other way.

---

