---
title: "PPC - Two simple ways to save power"
date: 2008-11-27
forum: Apple Hardware Users
---

### Post by stream303 on 2008-11-27
Want to keep your old power supply around a bit longer, or just contribute to the global power-saving effort?  There are two simple ways to do it:

1) Turn off blinking cursors. (*Even if you aren't running a terminal session!*) I read it somewhere about saving 2 watts of power, so I put a wattmeter on my ac outlet, and lo and behold - my G5 at idle went down from 90 watts to 88 watts.  Ok, 2 watts may not seem significant, but every little bit helps right? - especially if viewed in global terms.

I'm not in Ubuntu right now, but in Debian Lenny-Testing, and it is pretty easy:

**System > Preferences > Keyboard > General > Cursor blinking.**  Just uncheck it.

2) The second best way is to make sure your cpu frequency scaling is actually working.  For ppc, there have been numerous reports of the default powernowd not working correctly, with systems running full speed all the time - unless you manually reconfigure it.

One easy way to see the cpu frequency in use is to just go to the top panel in Gnome, and right-click it.  Now, Add-To-Panel, and select the CPU Frequency Scaling Monitor app.  It should now show up in the top panel.

If for some reason it never settles down when the machine isn't doing anything (and assuming there are no daemons eating up all the cpu time), you can reconfigure powernowd:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

About half way through are the instructions for fixing powernowd.

An even easier method is just to use **cpudyn** instead of powernowd.  It is as easy as merely using synaptic to download and install it.  It will take care of automatically removing powernowd, and installing cpudyn instead.

On my machine running full speed, I'm using about 106 watts.  When cpudyn kicks in and throttles the cpu to half-power, the system uses only 90 watts.  That is a 16 watt saving.  When I toss out the blinking cursor, I'm now at 88 watts for 18 watts total saving.  Pretty significant.

---

### Post by oswaldkelso on 2008-11-27
You may want to look at "powertop" also

---

### Post by stream303 on 2008-11-27
I dig powertop.  Some I've shown it to are amazed that it works on PPC - albeit without the cpu states being reported, but the advice it gives after taking other readings is very valuable.

---

### Post by giannimaria on 2008-11-29
Is the powernowd ppc fixing still necessary when running 8.10?

---

### Post by stream303 on 2008-11-29
It is still a problem when running Intrepid on my G5 iMac, as it was in Hardy and maybe even all the way back to Feisty. :)

I used gnome's cpu-frequency scaling monitor applet, and it always indicated that the system was running full speed - even when it should have been idle.

You could do it from the commandline, ie

```
cat /proc/cpuinfo
```

to see your current speed, but I didn't always trust that my keystrokes and command may have triggered it to full speed giving me a false impression that it was running that way all the time. :)

I used the fixes shown in the faq, but operation of powernowd was still a bit quirky for me, so I just downloaded and installed **cpudyn** instead with synaptic.

BTW - powernowd works out of the box for me with Debian Lenny-Testing.  However, I still prefer cpudyn for a lower-latency response, which many say that it also brings you to an idle-state faster than powernowd.  That's a whole performance issue debated elsewhere.. :)

---

