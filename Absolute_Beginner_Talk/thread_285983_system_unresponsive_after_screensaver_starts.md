---
title: "system unresponsive after screensaver starts"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by angelsneverdie on 2006-10-27
Hello - i just upgraded to edgy eft and have noticed that if i let my computer go idle for long enough that the screensaver comes on (ten min in my case) the screen turns black (not off, just black) and the computer becomes unresponsive (almost like the system is asleep - but doesn't respond to any keyboard or mouse movements)  I end up having to reboot.  i turned the screensaver off and it works fine.  

I don't really need the screensaver turned on - but don't like it when things that should work don't.  anyone have any ideas?

Thanks!
Mitchell

p.s.  I'm new to linux and have no idea what i'm doing, still trying to get dos commands out of my head and what not - so be gentle.

---

### Post by Malakia on 2006-10-27
Check the power options and see if it is set to hiberate or sleep that could be the problem. Than again it could be a bug in edgy since edgy was just released.

---

### Post by angelsneverdie on 2006-10-27
yes, forgot to mention that - that was my first instinct but the power save options are indeed turned off

-mitchell

---

### Post by CatKiller on 2006-10-27
A few people have reported that power management still kicks in even when it's turned off in the Gnome settings. I've never read one of those threads to the end to see what the solution is, though.

---

### Post by bulldog on 2006-10-27
Is CTRL-ALT-BACKSPACE working so you can logout and login without a reboot?

Did you install your graphic's driver and is it well configured?

[I just stick with Dapper for a while though :D ]

---

### Post by Tom_servo on 2006-10-27
Dont forget you can CTRL + ALT + F1 to drop to a terminal. Login with your username and password and do:

sudo /etc/init.d/gdm restart

This will restart you Gnome session and drop you back at the graphical login prompt. Its nasty but at least you don't have to pull the power lead :D 

To get back to Gnome session with restarting anything do CTRL + ALT + F7 and typically the graphical session lives there.

Good Luck

---

