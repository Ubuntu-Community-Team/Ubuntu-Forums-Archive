---
title: "Accidental PMU reset has caused bugs"
date: 2007-04-30
forum: Apple PPC Users
---

### Post by Starev91 on 2007-04-30
Alright, first the system specs, then the problem:

iBook Dual USB
256mb RAM
500 mHz powerpc g3 CPU
15gb hard drive
CD-ROM drive (cannot burn)

If more is really needed, I'm sure there's more I can dredge up.

Either way:

Earlier today, a rather spastic friend of mind wondered what the PMU button did.  Despite my asking her not to push it (I didn't know what it was at the time), and trying to prevent her from doing so, it got pressed.

Since then, Ubuntu (first 7.04,  then, after a reinstall, 6.1) has complained when I log into my account that Nautilus could not load, because Bonobo couldn't find the factory.  It advised killing Bonobo (which I didn't do) to solve the problem.  I later reinstalled Ubuntu (didn't have anything important on the computer, so the hard drive was wiped) to the same problem.  After a bit of research, I found that pressing the PMU "Resetting the Power Manager on any PowerBook or iBook will permanently remove a RAM disk, if present, and all of its contents." (Apple page on how to do it).

So I assume that the problem comes from the missing RAM disk, since that seems to be the perm. effect of the missing RAM disk.

Now, is there any way I can solve this problem?  (perhaps by somehow getting the RAM disk back?)

Hardware isn't exactly my specialty (*is a simple Java programmer who lets others think about such things unless he is merely reading about it, but will eventually (in a few years) get around to learning about hardware, after I get to learning C++*), so very very easy to follow instructions are good.  (For the record, I have an understanding of what RAM is, but not of what a RAM disk is  (other then a disk with RAM :P)  That ought to give you the idea of what kind of instruction I need).

Edited to add:

Also, ever since I installed Ubuntu, it hasn't been able to use my sound card.  If there's a known workaround, it would be appreciated, but it's not like i use sound all that often anyways.

---

### Post by LususX on 2007-04-30
you can try  to reset your PRAM, by holding down OPT, APPL, P, R on reboot. Hold those keys down until you hit the startup PONG 3 - 4 times.

---

### Post by Starev91 on 2007-04-30
> **LususX said:**
> you can try  to reset your PRAM, by holding down OPT, APPL, P, R on reboot. Hold those keys down until you hit the startup PONG 3 - 4 times.

Just tried it twice, no change.

I'm going to try reinstalling Mac osx and then reinstalling Ubuntu.  I have a hunch that Mac might be able to fix this, as when I read about what has happened with other PMU resets, it seems to have gone well with no bugs for those using mac osx.

It'll give me a chance to make the computer a dual boot anyways, which was my initial goal.

Other advice is still welcome, although no confirmation of if it worked or not will be available for a few hours :P

---

### Post by seatea on 2007-05-01
Take a look at this Apple technical support document: [http://docs.info.apple.com/article.html?artnum=95037](http://docs.info.apple.com/article.html?artnum=95037) It might be worth the time to reset the PMU the recommended way. It may be too that you have some  data  corruption as the result of  the accidental PMU reset. That should be fixed by your re-installation.

---

### Post by godsbane on 2007-05-01
did you try setting the time with the console? That fixed my bonobo errors after a pmu reset.

The following was stolen from another thread.
> 
This thread is for the benefit of users with iBook laptops and any other laptop that may have a problem with dropping hardware date and time.

Specifically, this addresses these symptoms:

Upon login to the standard Gnome interface, the following are encountered (posted by Arizona previously):

Error #1
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

Error #2
There was an error starting GNOME Settings Daemon. Some things, such as themes, sounds, or background settings may not work correctly.

Error #3
There was a problem registering the panel with the bonobo-activation server.
The error code is: 3
The panel will now exit.

The solution lies with the hardware clock.

NOTE:
If the laptop drops the hardware clock values, or resets to something like 1905 or something stupid, the cause may need to be addressed as well. (In my case it was the laptop crashing under OS9 when hybernating, remove battery to get it to startup and your date is gone)

When the errors are displayed (for simplicity sake), enter this combination:
[ctrl]+[option]+[f1]

This will open a virtual terminal.
Then, obtaining the correct time and date, enter the following command:
> sudo hwclock --set --date "MM/DD/YYYY hh:mm:ss"

To state the obvious (in case it's not): "Month/Day/Year hour:minutes:seconds"
I believe that this is the only accepted format.

That command sets the *hardware clock*
I think it'd be possible to simply restart at this point, but I decided to make the system clock match the hardware clock.
> sudo hwclock --hwtosys

then I checked it:
> date

And I restarted:
> sudo shutdown now
> sudo hwclock --hwtosys should be sudo hwclock --hctosys

---

### Post by Starev91 on 2007-05-01
Fixing the clock probably would have solved my problems, although using mac osx gave me my original goal of a dual boot (which I got distracted from when I realized how much fun I could have with ubuntu :P), which makes the computer much more useful to me as far as what I had wanted to use it for (instead of what I had been using it for).

Problem is solved.  (*feels a bit foolish for not using search to see if he could find it here*)

---

### Post by Ephry on 2007-05-03
One thing that work for me was shuting off the machine and letting it cool off. The with the network wire in, started the system. I was getting the same errors after leaving my Ibook in the case while it was turned on(yeah I know) The clock and everything else was fine. I do run a dual boot with Xubuntu and Ubuntu. 


Let us know how it works.


E

---

