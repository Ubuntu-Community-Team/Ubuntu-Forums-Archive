---
title: "idle CPU Usage at 7%"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by icedogchi on 2007-01-26
Greetings!  I installed Ubuntu 6.06 from DVD about a week ago.  First, thanks for making the install so easy!  I'm very amazed at how flawless the process was.  After I figured out the ERROR 18 from GRUB (I had to partition my 250G hard drive correctly), I was up and running.

I'm using an older computer, HP 7855 with 384M RAM.  Initially, I had a problem where the screen saver was very stuttery and would consume 100% of my CPU.  After a bit of research, I found a web page that indicated my onboard video card (82810 chipset?) would not run openGL at 24 or 32bits of color.  Basically, I had to edit my xorg.conf and change this to 16 bits and BAM! screen savers worked and would not consume 100% of my CPU (although some of the very flashy screen savers still chew up 30+%)

So, I let the computer sit idle for a week and checked on it from time to time to see that all was well.  I noticed that the CPU was consistently being used.  Anywhere from about 6% - 9% was in use according to the system monitor.  When I would move the mouse or open a window, the CPU would shoot up to 60-80% and then calm back down to the 6-9% range.

I would compare this to my Windows XP system running on a different computer.  The CPU there is reported at 0% when the system is idle and I get CPU spikes when moving the mouse/opening windows.

My questions are:
1)  Is it normal for the CPU on Ubuntu to be running at 6-9% even when idle?  The only process I see awake is some gnome window watching process (not at home so I don't remember the exact name).  I'm guessing this is what waits for me to move the mouse, etc, so it can respond.

2)  Is the system monitor on Ubuntu reliable and shows real CPU usage?  That is, I can trust that the 6-9% usage is real and not a bug in the reporting tool.

3)  Is comparing the idle Ubuntu CPU usage to an idle Windows XP CPU usage a reasonable thing to do?

Finally,
4)  How can I get an idle system to use less CPU on Ubuntu.

Total noob here, but trying to learn!  Thanks!
-JT

---

### Post by boredandblogging.com on 2007-01-26
Honestly, I wouldn't worry about it unless its somehow stopping you from using your computer.

I don't buy that XP is using 0%. Some application is probably polling or listening for input.

---

### Post by kosmic on 2007-01-26
Just post your 'top' results here. so we can see what we can shut down :)

Also you can try 'Xubuntu'

---

### Post by icedogchi on 2007-01-26
I kind of doubted Windows XP saying 0% CPU as well, but that's what it reports (obviously *something* has to be running waiting for input).

If 6-9% seems resonable, then I won't concern myself with the CPU usage.  Just seemed odd that it would be using that much CPU polling for input (or whatever it does when idle).  Gut feel was 1-2% CPU usage while idle would be more appropriate.

Thanks for the quick reply!
-JT

Kosmic - will do once I get home tonight.!!

---

### Post by punx45 on 2007-01-26
I'll bet there will be something gnome related in that top readout.   
My system at home is a PIII.   I am shelled in at the moment, so there is no gnome session running, and the processor is hovering around 1% use.   But when I am at home and running a gnome session it tends to idle higher, and spike when moving windows and stuff, even with an (albeit old) nvidia card and the nvidia driver.

If it isnt affecting usability or stability I would not worry about it.
I would be more concerned about the amount of RAM and the HDD thrashing for swap.

Like someone else said, try installing XFCE (or fluxbox) and thunar, and choosing that under the sessions button on the login screen.   My system tends to be less sluggish in an XFCE session.

---

### Post by icedogchi on 2007-02-06
How do I run the top command?  When I do:
>sudo top

I get a screen of changing numbers.


when I do

>sudo top > <some file>

The command never returns (presumably it's continually writting to the file).

Thanks!

---

### Post by boredandblogging.com on 2007-02-06
while top is running, hit q. That should stop it and leave the contents on your screen.

---

### Post by marx2k on 2007-02-06
You can also use the 'w' command - I use the 3 load averages there to figure out my true CPU load

---

### Post by old_geekster on 2007-02-06
> **boredandblogging.com said:**
> Honestly, I wouldn't worry about it unless its somehow stopping you from using your computer.

I don't buy that XP is using 0%. Some application is probably polling or listening for input.
I agree whole-heartedly.

In Windows the idle CPU usage can be very high at times (up to 100%), because it is doing tasks that are required in down-time.  So, I wouldn't be a bit surprised to find this is the same in Linux.

---

### Post by icedogchi on 2007-02-09
Looks like the top command reports a different CPU usage than the system monitor on Ubuntu.  I (hopefully) attached a screen shot of the top command.  As you can see, this shows a MUCH lower load on my CPU.

Thanks for the help!  I'm hazarding a guess that the system monitor was chewing up CPU to display the graphical window.  Sound right?

Again, thanks!

---

### Post by jordanmthomas on 2007-02-09
I'd say that is a good guess.  The same thing happens on my computer.

---

