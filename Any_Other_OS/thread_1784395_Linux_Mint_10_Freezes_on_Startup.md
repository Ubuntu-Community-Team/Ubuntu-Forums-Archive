---
title: "Linux Mint 10 Freezes on Startup"
date: 2011-06-16
forum: Any Other OS
---

### Post by Curse on 2011-06-16
My gf has been using Linux Mint for about 2 months now after I convinced her to ditch windows. It has been working great up until now, but today it decided that instead of acting normally, it is going to give us issues.

Basically, when you start it up, select Mint from GRUB, it acts normally until, when you'd get a login screen, you get a screen that shows a Panel bar at the bottom with the Time and Power button at the far right, nothing on the left, and in the middle is the User-Laptop splash square that you'd click to enter password and log in.

It's like her computer is half logged in, half logged out.

I have no idea what to do, help?

---

### Post by Curse on 2011-06-16
Also worth noting that when I put the Mint disk in and have it boot from that, once it is fully booted I cannot run any programs and trying to open any folders simply refreshes the desktop (or an effect similar to refresh - the icons disappear and reappear after a split second)

---

### Post by tgalati4 on 2011-06-17
Run memtest from the LiveCD overnight.  You need 30 complete passes to validate the RAM.  If the RAM is bad, then strange things can happen.

---

### Post by Curse on 2011-06-17
I was thinking it might be the RAM too... will do.

Any other ideas?

---

### Post by mastablasta on 2011-06-17
Well it's odd that you can't boot from livedisk. it means it's not the hard drive. So inless there are freezes (which could indicate bad capacitors) then all that is left is graphics card and ram. CPU seems to be working. unless it's getting overheated. but behaviour is strange.
 
BTW do oyu hear any additonal or unusually long beeps on boot? it should be one short beep.

---

### Post by Perfect Storm on 2011-06-17
Moved to Other OS/Distro Talk.

---

### Post by Curse on 2011-06-17
No beeps, and it does boot with live disk, I just can't do anything aside from open the Applications menu up. It isn't overheating, and it appears that the freeze always happens at that specific point. 

Running memtest right now, we'll see what it comes up with :x 

Thank you for your help!

---

### Post by Curse on 2011-06-18
It has gone through 31 tests, so far no errors :/

---

### Post by Spice Weasel on 2011-06-18
Can you start X without the display manager?

(Press ctrl alt f2, log in, type *sudo service gdm stop* and then *startx*.)

---

### Post by Curse on 2011-06-18
I'm not able to get to any of the TTL commands. At least not after it has hung up.

Or should I try to get to them while it is at the GRUB screen or ? 

BTW, I just stopped it at 50 passed and 0 errors. Going to pop the HDD into my desktop to see if it gives me the same issue.

---

### Post by Spice Weasel on 2011-06-18
Try before the login screen loads.

---

### Post by Curse on 2011-06-18
Ok, just tried that - it would go to a flashing _ but I could not type anything and after a minute it just continued on to the point where it hangs :/

---

### Post by Curse on 2011-06-18
Just popped the HDD into my desktop computer and booted from it..... does the same thing! Ugh!

---

### Post by tgalati4 on 2011-06-20
Do you have a rescue kernel to boot into?

---

