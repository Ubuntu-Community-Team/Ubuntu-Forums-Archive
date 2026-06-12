---
title: "Please Help. keyboard and mouse lockout?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by MrTao on 2007-03-07
Hello everyone,

I made the shift from windows about a week ago and can tell you i am happy i did. 
Even more so once i get my head around the little things :) For instance, if i leave my ubuntu idle for anything longer than a few minutes, i seem to get locked out. i see people chatting to me and vlc playing however i can not do anything?! 

it is really quite distressing.

can anyone tell me how to obtain access once this has happened i would be much appreciated...or turn it off?

thank you in advance.

---

### Post by chewearn on 2007-03-07
There are cases where the screensaver caused 100% CPU.   Maybe you can try turn it off.

Or, open up the System Monitor, leave the window on top, see if any process is locking-up the system.

---

### Post by MrTao on 2007-03-07
thanks, i'll let you know what the results are.

---

### Post by pandu.rs on 2007-03-07
if you are familiar with command line, u can press ctrl+alt+f1 (actually f1 thro f6) to get into a console and then see what is going on (if you are familiar with command l.

---

### Post by MrTao on 2007-03-07
unfortunately the suggestion about using ctrl+alt+F1 isnt an option as my keyboard is even unresponsive to that. last night i kept my system monitor open and did notice a screensaver use 100% cpu. i will try and post the specifics tonight.

thanks for the help.

---

### Post by MrTao on 2007-03-08
ok, so i set it up so VLC was running so i could tell it hadn't crashed and the system monitor was open aswell. 

i started the test at 6.48 pm (active processes with cpu usage were; gnome-system-monitor 3/4%
xgl 1/3%
vlc 0/1%
with beagle jumping in every now and then with 14/15%)

i waited until 6.58 pm with no new processes (ie. the screensaver) being activated. However when i attempted to use my keyboard and mouse it was the same thing, no response.

if i continue moving the mouse there is no lock up... is this a security measure? 

any more ideas on how to disable or reactivate once this occurs would be much appreciated.

---

### Post by pandu.rs on 2007-03-08
Try disabling the screensaver

System->Preferences->Screen Saver
Uncheck both activate screensaver and lock screen options

Also disable the power management features

System->Preferences->Power Management
Change both the sliders to Never

Now check if the problem is gone

---

### Post by MrTao on 2007-03-08
i have made sure power management is set to never on both bars and the screen saver is set to identify idle as 2 hrs, with no boxes ticked. however it is still becoming non responsive after a few minutes if idle and then it goes to a blank screen, i can still hear sound from vlc however... any other ideas?

has anyone else come across this issue? is it possible to definitively disable screensaver or power manager? 

i am lost. i hope there is a solution, i dont want to have to use windows :(

---

### Post by Bartender on 2007-03-08
What's the video card?  My ATI 9200SE would lock up the PC as soon as screensaver came on.  And I couldn't turn off screensaver because just going to the screensaver utility would lock up the PC!!  Since I knew nothing about tweaking the system I bought a plain vanilla Nvidia card & problem went away

---

### Post by MrTao on 2007-03-08
i have 2 nvidia 7900's only one is being recognised though.

---

### Post by chewearn on 2007-03-08
It seems not to be a screensaver problem, after your test not showing a 100% CPU, even as the mouse and keyboard lock-up.

What mouse and keyboard are you using (usb or ps2; exact part/brand)?  Maybe someone in this forum has a similar experience.  Any chance you can find another mouse/keyboard and replace?  Or you could temporary borrow one to test.

---

### Post by MrTao on 2007-03-08
sounds like a plan , ill get the info, do the test, and post the results tonight. 
thanks for the help again.

---

### Post by MrTao on 2007-03-10
your idea of changing the keyboard and mouse just might of done the trick i was originally using a logitech G15 (which i had previously had trouble with, constantly typing 3's for no reason) and a new logitech MX400 mouse both of which were using USB.

Bought a cheap microsoft mouse and keyboard, thought i'd try the ps2 ports instead and presto! no more lock out after 5 minutes of idle. 

on a side note i was looking at my xorg.conf and noticed under mouse it had ;
Option		"Protocol"		"ExplorerPS/2"    

would this have something to do with the problem?

under keyboard there was also ;
Option		"XkbOptions"	"lv3:ralt_switch" 

i dont know what that one means, just a thought.

thanks for your time and patience in helping me through this issue, it was much appreciated.

---

