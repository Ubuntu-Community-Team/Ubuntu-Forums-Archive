---
title: "Really REALLY SLOW"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by w1zer on 2007-05-09
Hi all

I have just started using linux on my new PC and am having problems.  The whole system is extremely slow.  The PC is a brand new HP DC7700p.  Opening windows, programmes and using the internet is dead slow.  

Can anyone help me diagnose the problem?

---

### Post by PartisanEntity on 2007-05-09
You need to give us much more info, what specs does your system have? which version of Ubuntu did you install? Did you install any additional software?

---

### Post by starcraft.man on 2007-05-09
Ummmm, your problem description is well very vague... not to mention relative. I mean, there have been numerous topics comparing windows and ubuntu and often people are thinking/finding ubuntu to be just a bit slower.

Can you give us actual numbers of how many seconds it takes you to load something? Like openning open office writer and firefox, those are two good standards of how slow you are >.>. Like I can open Openoffice in 5-6 seconds cold usually, sometimes less, and firefox is faster at just 2 seconds.

---

### Post by w1zer on 2007-05-10
ok

HP DC7700p
P4 Dual 3.4GhZ
1GB Ram
Intel 82945G Express Chipset Family Display

A Click on a menu icon will take about 3-5 seconds to display the Menu.  Firefox takes roughly 10-20 seconds to load.  openoffice takes about 40-50 seconds to fully load.  

This is a clean install of ubuntu 7.04 with nothing other than the packaged software.  

In comparison to XP on the same machine this is extremely slow and sluggish.

---

### Post by bikeboy on 2007-05-10
What you describe there is definitely not normal. My PIII with 384mb of ram is much faster than that.

Maybe something is "stealing" all your cpu time for some reason.

Try looking at System > Administration > System Monitor...if you can stand the wait :P

If that's too slow. Applications > Accessories > Terminal. Then type "top" without the quotes. q to quit.

---

### Post by Ozeuss on 2007-05-10
i suggest putting the system monitor applet on the toolbar, monitoring CPU, memory and swap. that way you can follow the system's condition, and see if it a memory thing or a cpu thing.
check through system monitor that it recongnizes all of the 1 gig memory, and swap.
finally, you can type "uname -a" and "free" to see what kernel is used, and memory respectively.

---

