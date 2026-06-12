---
title: "Strange Sound Issue under edgy/Thinkpad T60"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by faylix on 2007-04-08
After install - sound worked fine. 

mean time: Installed some new programs, mostly libpcap stuff network tools, etc, nothing to do with sound. 

First occurance: Tried to play a DVD with totem (followed instructions under restricted formats). Sound stopped working.  

Now: About 50% of the time i turn my computer on theres no sound. Alsamixer shows sound all the way. Ubuntu's sound icon at the top shows it at 100%, rhythem box plays - but no sound. 

If i restart, still no sound. If it turn it off, let it sit for a bit, and turn it back on, sounds back. I've tried restarting alsautils with the init.d script, no luck. 

:( :confused: 

Laptop: lenovo T60, intel sound card. 

thanks guys. 

-J

---

### Post by frankchen on 2007-04-14
I met almost the same issue, and mine is a t60 15.4inch widescreen. Anyone can help? Thanks.

---

### Post by rikersmailbox on 2007-06-12
I am having a very similar problem with my T40. The sound was working perfectly for a while, but I woke up this morning and I got nothing.

Did anyone find out what was going on?

---

### Post by rikersmailbox on 2007-06-12
ok, after some searching around, I think I found the problem.

I believe its Bug #80893. Apparently, after hibernation the sound stops working for whatever reason I don't understand, however the solution to this is simple. The system just needs a cold startup. A reboot won't do anything, though. To fix it, turn off the computer completely and turn it back on. It worked for me. Here is a link to the page that helped me. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

---

