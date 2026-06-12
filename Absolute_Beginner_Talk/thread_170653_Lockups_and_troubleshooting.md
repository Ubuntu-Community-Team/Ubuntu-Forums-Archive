---
title: "Lockups and troubleshooting"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-05-05
I have been happily working for a few weeks with Ubuntu. Everything was going great until today.  Suddenly I'm getting system lockups that don't respond to CTRL-ALT-F2 or CTRL-ALT-BACKSPACE.  In two instances tonight, the keyboard and mouse locked.  In the third instance, the keyboard locked but not the mouse.  In all cases, I had to power down the computer in order start again.

Complicating this whole issue is that this is a new machine, and it is always possible I'm having some sort of hardware failure.

I started having the trouble under KDE and switched to Gnome, but alter a period of working Gnome locked up too.

What I'm looking for are some suggestions on how to troubleshoot this problem.

I tried e2fsck -f -p to check for corruption.

Since on two of the lockups the screen became distorted, I have tried dpkg-reconfigure xserver-xorg from the rescue boot screen.  I'm now working, but I don't know for how long.

What are my other options, ASSUMING that the issue is a piece of corrupted software and not a hardware failure?  Is there a command to reinstall the system software?

And is there a recommendation for a utility that will test the hardware -- video and memory inparticular.

Thanks in advance for any help.

---

### Post by Sef on 2006-05-05
Memtest86 will check your memory, but it needs to run for a while.  Best to do it overnight.  I believe it's in grub, so just hit esc when you first boot up.  

NOte: the test will keep running and running, so just turn it off after about 8 passes.

---

### Post by Borniet on 2006-05-05
I would recommend a mem-test too... Used to have the same problem, was due to a broken motherboard, but it became clear by doing the memtest.
Or: does it happen when doing something specific? My laptop now still locks up from time to time, due to the WLAN card. I noticed because my connection sometimes just dies, and restarting the network simply locks up everything. Sometimes I can still reboot normally (which then is the only thing it still does), and I can see the errormessage regarding the wlan card.

---

### Post by richbarna on 2006-05-05
I had this on an old pc about 18 months ago, it was a worn out mother board. As soon as it got warm (20 minutes) Mouse and Keyboard locked.
I've heard it's quite common on old pc's apparently. (nothing lasts forever).
But for this to happen on a new pc sounds like faulty hardware. (They don't make 'm like they used to)

---

### Post by jlhughes on 2006-05-05
Ran Memtest86 three times. The first and third times no errors were reported. One test ran seven hours; the other through 5 cycles.  I'm unsure what happened to the other test. I left the room for several minutes and when I returned the power to the monitor was off.  Eventually I got the power back on, but I don't recall what I did to get it back. 

I really don't want the problem to be hardware, but then I guess when you buy a low-end product you have to expect low-end results some times.

---

### Post by Jason_25 on 2006-05-05
It's sounding more and more like a hardware problem.  Check your cpu and video card temps.  Superpi on windows and sprime on linux is a good cpu/memory stress test too.

---

### Post by jlhughes on 2006-05-09
Since I started this thread I've been looking at possible software fixes. Almost all of my lockups occurred while using Firefox. Since the machine was left on for days at a time and the crashes days apart, I was interested to discover that Firefox has a memory leak. I found a simple fix  [ here]("http://www.freerepublic.com/focus/f-bloggers/1327586/posts")

I haven't had a lockup since (knock on wood).

---

