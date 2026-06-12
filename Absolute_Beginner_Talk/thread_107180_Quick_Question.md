---
title: "Quick Question"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by herrpoon on 2005-12-22
Hi, when I go away for weekends or what-not, I'll leave my computer on for downloads or whatever, but what I want is to be able to close gnome or at least turn it off temporarily and then turn it back on when I get back.  Any ideas?

---

### Post by Emerzen on 2005-12-22
I'm not sure exactly what you want to do, turn the computer off or just the GUI?  In any case, you could schedule a cron job --> sudo init 6 will turn the PC off, init 0 i think reboots, init 1 or 2 is just kernel mode...obviously, I've not done this but should be possible.  Look up how-to on cron jobs and the init run level.

---

### Post by xtacocorex on 2005-12-22
Do you still want the GUI programs that download to work while Gnome is turned off because I don't think that'll happen.

You could always turn off X by using:
```

sudo init 1

```

That takes the machine to single user mode on the command line.

To get back to X (assuming still in single user mode):
```

init 3

```

Edit:
towson2003's method is probably a little safer than going to runlevel 1, which is for system maintenance on research I just did.

---

### Post by towsonu2003 on 2005-12-22
[QUOTE=herrpoon]Hi, when I go away for weekends or what-not, I'll leave my computer on for downloads or whatever, but what I want is to be able to close gnome or at least turn it off temporarily and then turn it back on when I get back.  Any ideas?[/QUOTE]
```
sudoe /etc/init.d/gdm stop
``` will stop X (thus gnome) and ```
sudoe /etc/init.d/gdm start
``` will start it, but **once you stop X, you will stop all prgrams X uses** including you GUI download manager...

I don't think this is what you're looking for...

---

### Post by herrpoon on 2005-12-22
Ahh excellent, I use the command line version of bittornado so that latter one should work a treat!  Thanks for all your help :p

---

### Post by bscbrit on 2005-12-22
You can always switch to runlevel 1 and then run the machine using a simple terminal screen while you are way, and then switch back to runlevel 2 when you return.  But what kind of updates are you trying to download?  Your computer is fully functional as long as it is running - it doesn't matter whether you log on or not.  And if you haven't logged on, Nautilus will not be running.  Could the downloads be done by a cron job running automatically, say, once a day?  Why do you have to log on?  You cannot be inputting any key presses or mouse movements so what does logging on achieve?

---

### Post by herrpoon on 2005-12-22
Sorry, I didn't explain myself very well.  Basically I leave my computer on so I can download torrents, up until now I've been leaving the X-session running but since there is no need (I use the bittornado command line with a web-interface) I thought I might aswell turn it off.  I thought it might save a bit of electricity and processing power.

(Probably doesn't save much but what the hey!)

---

### Post by bscbrit on 2005-12-22
It certainly won't save electricity but it might save processing power - however, to what purpose?  Saving processing power in one area is only useful if you can use that power somewhere else.  In this case - it is wasted.  Your computer will spend 99,9% of each day waiting for data to arrive.  Whether, in between data arriving, it also runs Nautilus or nothing at all is probably irrelevant.  You will save more by switching the screen off by its power switch - it will not be showing any desktop or terminal then!

---

### Post by estel on 2005-12-22
Turn on BOINC as well, to make it worthwhile ;)

---

### Post by herrpoon on 2005-12-22
[QUOTE=bscbrit]It certainly won't save electricity but it might save processing power - however, to what purpose?  Saving processing power in one area is only useful if you can use that power somewhere else.  In this case - it is wasted.  Your computer will spend 99,9% of each day waiting for data to arrive.  Whether, in between data arriving, it also runs Nautilus or nothing at all is probably irrelevant.  You will save more by switching the screen off by its power switch - it will not be showing any desktop or terminal then![/QUOTE]

I suppose, it just seems silly to me to have something "on" when you're not actually using it ;)

---

### Post by bscbrit on 2005-12-22
estel's suggestion is a good one.  You can put all the 'spare' processing power to good use for various types of scientific research.  You cannot do anything with the processing power yourself but that does not mean it has to be wasted.  My own view is that the BOINC and Ubuntu communities have a similar philosophy - they both like to help others.

---

### Post by towsonu2003 on 2005-12-22
[QUOTE=herrpoon]Sorry, I didn't explain myself very well.  Basically I leave my computer on so I can download torrents, up until now I've been leaving the X-session running but since there is no need (I use the bittornado command line with a web-interface) I thought I might aswell turn it off.  I thought it might save a bit of electricity and processing power.

(Probably doesn't save much but what the hey!)[/QUOTE]
From another point of view, not running X all the time unattended is probably a good idea bc. it might end up crashing the computer due to some unforeseen bug (a memory leak at the least). Your processor will also be happy that X is off :)

I was alos gonna say servers don't run X, so there should be a reason to that... But I am too lazy to research that, and without research, I'm sure someone would kick my a** sooner or later ;)

I don't know anything about BOINC ([http://boinc.berkeley.edu/](http://boinc.berkeley.edu/)) but it sounds nice. However, I wouldn't just 'turn it on' unattended either. 

PS. While you are gone, turn off the monitor :)

---

### Post by bscbrit on 2005-12-22
yes, that's a good point but I do not have too many concerns regarding X.  I have systems that have been up for several months that haven't yet fallen over so I don't think that its currently a problem.  But with another update, different versions etc, who knows what might happen.
I can allay you security concerns regardin BOINC (seti@home/folding etc).  They have thousands (millions?) of users and there have been no reported issues.  I wouldn't do it with my W2K system though..... (Thats not a troll, simply my view based on my experience!)

---

### Post by estel on 2005-12-23
My windows system runs BOINC as much as Ubuntu :)

---

