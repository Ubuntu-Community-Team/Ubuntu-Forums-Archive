---
title: "Core Clock Speed Fluctuates, too much"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-24
I've got a Q6600 processor that I've overclocked to 3.33ghz, and I've been watching the processors clock speed using Conky and it fluctuates a bit too much between 2.22ghz and 3.33ghz...

I understand that it's normal behavior for a processor to throttle or reduce it's speed (multiplier) at times to save power/heat and extend the life of the chip, but when I've got the processor loaded, it shouldn't be fluctuating, it should stay at 3.33ghz (correct) ?

Here are two screenshots of what I mean, on the left side of the screen you will see ***top*** running in the terminal on the right side of the screen you'll see ***conky*** running.  The first screenshot shows the core's clock at 2.22ghz and the second screenshot shows 3.33ghz. These screenshots were taken back to back, within a few seconds of one another.

[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/topconky-2220core.jpg[/IMG]

[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/topconky-3330core.jpg[/IMG]

p.s. I have a WinXP partition on this machine that I dual-boot into (only for testing purposes) and everything is running fine in XP, when I put the system underload it stays pinned at 3.33ghz (as it should), so why is it bouncing back and forth in Ubuntu?

---

### Post by dcstar on 2008-02-24
> **B/-\ssKozz said:**
> I've got a Q6600 processor that I've overclocked to 3.33ghz, and I've been watching the processors clock speed using Conky and it fluctuates a bit too much between 2.22ghz and 3.33ghz...
.........
p.s. I have a WinXP partition on this machine that I dual-boot into (only for testing purposes) and everything is running fine in XP, when I put the system underload it stays pinned at 3.33ghz (as it should), so why is it bouncing back and forth in Ubuntu?

Both those shots show your system at over 60% idle, Linux will throttle back when there is so little load.

---

### Post by BassKozz on 2008-02-24
> **dcstar said:**
> Both those shots show your system at over 60% idle, Linux will throttle back when there is so little load.
Hmm, I assume your speaking of the **61.2%id** number in top? (I am new to Ubuntu)
if so, I didn't notice that until you pointed it out... and how is that number calculated? because I know the one process I have running that is working hard is VirtualBox, and I have a Guest OS running multiple CPU intensive apps, so it would be beneficial for VirtualBox to have 3.33ghz running to it vs 2.22ghz? is there a way to FORCE max corespeed?

BTW, is VirtualBox not support multiple core compatible? how come it's not stressing more cores to keep this at 3.33ghz?

---

### Post by BassKozz on 2008-02-24
:bump: ):P

---

### Post by BassKozz on 2008-02-24
This is happening even if the idle is less then 60%, in this screenshot idle is at 43%:

[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/topconky-2220.jpg[/IMG]

---

### Post by BassKozz on 2008-02-26
:bump: 
should I post this in another forum?
Can a moderator help me and move this to the [General Help](http://ubuntuforums.org/forumdisplay.php?f=131) section... this might be too advanced for "Absolute Beginner Talk"

---

### Post by BassKozz on 2008-02-28
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/topconky-2220again.jpg[/IMG]
Anyone help me out... 20% idle, and it's still throttling down to 2220mhz :confused:

---

### Post by igknighted on 2008-02-28
Right click the panel, click add to panel, then scroll down and add the cpu frequency scaling monitor.  If you really don't want it throttling down like that (throttling is recommended), then right click that applet and set the power to 'performance'

---

### Post by Fred_E _krugar on 2008-02-28
In your Bios, do you have your CPU throttling disabled??

---

### Post by futureproof on 2008-02-28
i have a q6600 (95W version) overclocked to 3.1Ghz, it sits at 1.6Ghz at idle.  Even playing games nowhere near maxes it out.  Try running SUPER PI to 50 million places and see if it fluctuates during that process,  it will max out 1 core on your CPU for sure.   I dont know if there is a multi core version available.

---

### Post by BassKozz on 2008-02-28
> **igknighted said:**
> Right click the panel, click add to panel, then scroll down and add the cpu frequency scaling monitor.  If you really don't want it throttling down like that (throttling is recommended), then right click that applet and set the power to 'performance'
Thanks for the tip... it's not so much that I "*don't want throttling*" I am just trying to understand the parameters on how the computer knows when to throttle up&down... I didn't expect it to be done as often as I've been noticing... especially when running at only 20% idle compressing 10gigs worth of files using 2 different p7zip compression processes :neutral:
> **Fred_E _krugar said:**
> In your Bios, do you have your CPU throttling disabled??
Nope

---

### Post by Fred_E _krugar on 2008-02-28
If it is not disable then that could be causing it to throttle down. Just try disabling it, and see what happens.

---

### Post by BassKozz on 2008-02-28
> **Fred_E _krugar said:**
> If it is not disable then that could be causing it to throttle down. Just try disabling it, and see what happens.

I'd rather not disable it...
I don't mind it throttling down when I am not using the computer, but when I am trying to get the best performance I'd rather not have it throttle down during LOAD...

I guess what I am getting at it is, I am trying to figure out what/when determines the throttling of the CPU? Is there a certain amount of LOAD required to keep it from throttling down?

---

### Post by BassKozz on 2008-02-28
> **igknighted said:**
> **Right click the panel, click add to panel, then scroll down and add the cpu frequency scaling monitor.  If you really don't want it throttling down like that (throttling is recommended), then right click that applet and set the power to 'performance'**
I did that and I added one for each core, but when I right click it doesn't show and option for setting ***the power to 'preformance'*** :confused:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/cpufreqscaling.jpg[/IMG]

---

### Post by igknighted on 2008-02-28
> **B/-\ssKozz said:**
> I did that and I added one for each core, but when I right click it doesn't show and option for setting ***the power to 'preformance'*** :confused:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/cpufreqscaling.jpg[/IMG]

Weird, mine doesn't have it either... maybe it was the KDE scaling monitor that offered to configure it?  I have no idea how to do it in gnome i guess...

---

### Post by Fred_E _krugar on 2008-02-28
On all the Overclocking forums that I frequent they all suggest that throttling and OC do not play nicely.

---

### Post by warrior24 on 2008-02-28
not to hijack your thread  but do you mind telling me what program that is the one in red.


NVM I read it more carefully conky stupid me.

---

### Post by BassKozz on 2008-03-04
Someone over at the recommended I try Folding@Home to stress the cores and see if it bounces back and forth between 2.22ghz and 3.33ghz;

[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/FAH-conkytop-2.png[/IMG]

Yup, it still does :(
In addition to the [Abit Forums]("http://forum.abit-usa.com/showthread.php?p=931211"), I also posted this problem on [[H]Forums]("http://www.hardforum.com/showthread.php?t=1280760") and I am still getting mixed reviews;
Some say turn the throttling features of my Q6600 OFF, and still others say it's better to leave them on :confused:

---

