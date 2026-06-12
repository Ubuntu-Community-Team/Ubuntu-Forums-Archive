---
title: "Wow, Lots of freezing"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by doyve on 2007-07-08
I've just installed Ubuntu 7.04 (feisty? I think that's what it's called...) from the text-based cd as the live-cd kept hanging on me. And now ubuntu is hanging on me (screen just freezes and I have to reboot) for the same reasons (so it would seem).

I think it's my built in ethernet. I had a look in /var/log/messages and it said something about ../../../eth0 before the time of the hang. I tested this (it seemed to crash at random intervals) by disconnecting my ethernet cable and just playing gnometris, which was quite fun, I got 5000 something. Anyway, is there an easy way of sorting this out? (also I think my graphics card causes some crashing as I previewed a screensaver which made it hang and the screen goes completely white (apart from the cursor) when I turn on window effects).

Any insight is mucho appreciated! :)

---

### Post by nvteighen on 2007-07-08
Let me remind you that no matter how cool window effects are, they are still beta software and the best is not to use them...

---

### Post by DM was on fire! on 2007-07-08
Almost sounds like the same problems I'm having with freezing and segmentation faults.
Do a Memtest (which should be available via GRUB) and see if it says anything. :D That's the only info I can give you, since I haven't tried anything else (and I shut Memtest off halfway XD).

---

### Post by Old Pink on 2007-07-08
Sounds like a graphic card driver problem. :) 

What graphics card are you using?

---

### Post by doyve on 2007-07-08
It's not a graphic card driver problem, although... ok well half of it is.
I have 2 graphics cards ATI X1950pro and a nVidia geforce 7300 LE. The x1950pro makes the system hang when I do the window effects. So I thought, hm change it over to my other one (I don't have them both in the pc at the same time). So i used that and it asked me to update the driver for it which i did, it downloaded the driver and worked fine (but it said that the software was unsupported so i'm kinda confused as it worked anyway). So yeah, I have the visual effects, they work fine.

HOWEVER, the real issue of linux freezing still is still a problem (despite graphics cards) So I'm still thinking it's a network problem. Sometimes linux will just hang on loading (not at the bar but with the circly cursor).

I'll try a memtest and see what it says.
Cheers peeps

---

### Post by sailor2001 on 2007-07-08
check  speedtest.net to see if you're getting your proper bandwidth    My isp has been doing a lot of playing around lately that really screws me up.

---

### Post by doyve on 2007-07-08
I ran a mem test and nothing came up. I tried booting with my network cable unplugged again but it crashed when loading again. I'm really running out of ideas as to what's causing thigs.

---

### Post by doyve on 2007-07-08
If it helps here's a detailed hardware list.

Dual 2.4ghz (Intel C2D conroe)
2x 1gb (G.Skill running at 800mhz)
DFI Infinity 975X/G 
 - Intel 975x northbridge chipset
 - INtel ICH7R southbridge chipset
 - Realtek ALC882 high def. audio chipset
 - Realtek RTL8111B PCIE Gigabit LAN
200gb Seagate (barracuda?)
250gb samsung spinpoint (not being used, solely for os x)
nvidia 7300 LE graphics card (or a ati x1950pro 256mb - but this one is less supported i think)

I think that's about it for what's in the box.
Hope that will help solving the issue

---

### Post by doyve on 2007-07-08
Ok well, there seem to be no ways of fixing this. I'm downgrading to Edgy to see if that will solve my problems.

Thanks all!

---

### Post by Talon2 on 2007-07-08
If you are comfortable with changing BIOS settings you might consider changing some of your BIOS settings to more conservative values.  Changing one at a time then testing would help you discover which settings makes the difference if it is a BIOS setting that is the problem.

I had a friend that was having about the same problem as you.  The specific fix in his case was not something I would expect:  I changed the system memory from dual channel to single channel mode.

His system uses DDR memory and if you have a matched pair and put the sticks in specific slots the memory will run as dual channel which supposedly is faster.  I had tested using memtest several times but I was determined to get to the bottom of his problem.  I took both memory sticks out to clean the contacts.  When I replaced the sticks I put them in the slots to enable single channel.  His system has now run for weeks with not one single freeze.  The system is a rock.  Evidently there is a timing issue in there somewhere.

Good luck.

---

