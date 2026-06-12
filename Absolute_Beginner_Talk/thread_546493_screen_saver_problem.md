---
title: "screen saver problem"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by buffylette58 on 2007-09-08
i'm trying to kick back and watch some futurama, but the screen saver comes up every 10 mins (exactly), just a blanck screen saver, i have to move the mouse every 10 mins and it is really annoying. I have already unticked the make computer idol box in the screen saver settings and deactivated any power management settings, so now i have no idea what else it could be, please help:(

---

### Post by dpar on 2007-09-08
I realize this may be a dumb question, but have you turned the screensaver off??

---

### Post by tak1150 on 2007-09-08
I had the same problem when I was using Totem movie player and compiz fusion at the same time. I switched to VLC and no more problemo!

You can get VLC easily from automatix2 (might be able to get it from synaptics too)

---

### Post by buffylette58 on 2007-09-08
i think that could b it! i have CF and totem. i'll try VLC...

thanx heaps!

---

### Post by buffylette58 on 2007-09-09
hey! back again!! the same thing's happening...

it happens with mplayer too 

any other ideas? something to do with CF maybe?

---

### Post by asmoore82 on 2007-09-09
> **buffylette58 said:**
> hey! back again!! the same thing's happening...

it happens with mplayer too 

any other ideas? something to do with CF maybe?

are you on a laptop?

---

### Post by buffylette58 on 2007-09-09
nope desktop... this is really annoying...i hav my little brother in here to get up n move the mouse every time it happens! :p

---

### Post by BatsotO on 2007-09-09
have you try to terminate the gnome screen saver or xscreensaver (whichever you use) or adjust the power management

---

### Post by buffylette58 on 2007-09-09
i tried killing the screensaver and power management processes, and its STILL hapnin! :mad:

---

### Post by buffylette58 on 2007-09-09
bump

---

### Post by bobpur on 2007-09-09
It's not a conflict with Lil bro is it? Borrow the neighbors kid and see if that helps:) Also, gender and age might be a problem. Your girlfriend / wife busy? Do not use both together as the inherent conflict could destroy your computer, your peace of mind and your bank account:)
Seriously, other than what's already been mentioned, I'm at a loss.

                                                           Good Luck!

---

### Post by tak1150 on 2007-09-09
CF has its own screensaver feature... Could that be it?

---

### Post by buffylette58 on 2007-09-10
> **bobpur said:**
> It's not a conflict with Lil bro is it? Borrow the neighbors kid and see if that helps:) Also, gender and age might be a problem. Your girlfriend / wife busy? Do not use both together as the inherent conflict could destroy your computer, your peace of mind and your bank account:)


na, the li'l bro' does an a'ite job movin' the mouse!

> **tak1150 said:**
> CF has its own screensaver feature... Could that be it?

yea possibly, i cant seem to find anything about screensavers tho, in ccsm?

---

### Post by G-forze on 2007-09-10
I have the same problem. Unbelievably annoying when watching a two hour movie.

---

### Post by tak1150 on 2007-09-10
Yes, screensaver is under "Extras" of CompizConfig Settings Manager.

I know we've been through this already, but are you sure that the problem happens with VLC player?

---

### Post by buffylette58 on 2007-09-11
yea positive, happens in mplayer too :( after exactly 10 mins each time

ive unticked 'activate screensaver when computer is idle' in the screensaver settings
ive chose 'never' turn off display for both instances in the power management settings

and under my extras in CCSM i only have: annotate, benchmark , screenshot, splash and window previews... no screensaver...its a newish version of CF

---

### Post by Chris S. on 2007-09-11
Quick sanity check if you are using the Gnome screensaver:  type gconf-editor in the terminal, then go to apps->gnome-screensaver.  Try changing settings from there.

The screensaver appearing is the same as the one you have chosen in gnome screensaver or xscreensaver?  The CF screensaver has far fewer choices (like rotating the cube or flying windows) last time I checked so it should be easiy to distinguish.

---

### Post by buffylette58 on 2007-09-11
heres a screenshot of that for ya.

it always resorts to a blank/black screensaver, nothing else

---

### Post by Chris S. on 2007-09-11
Bizarre!  Try setting the cycle_delay to a high number.  Like ten thousand.

---

### Post by buffylette58 on 2007-09-11
nope, that didn't help either :(

this sux :p

---

### Post by Chris S. on 2007-09-11
If killing the screensaver and power-management doesn't do the trick, then there must be another process.  You could check your /etc/crontab or /etc/cron.X directories for anything someone might have snuck in on you, but that's unlikely.  You could scan through ps -e for any suspicious looking processes, or even start killing them off one by one to narrow down your search.  Make sure that if you kill a program, it doesn't start up again afterwards.

Hmmm, if you want to play dirty, you could write a program to send XFakeKeyEvents every few minutes to keep it awake. :D

---

