---
title: "Couple more questions"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by scriptsales on 2007-11-08
:)
Hi Gurus,

Got Ubuntu installed on my Toshiba M70, everything works just fine, even Wireless networking!

Now, here goes:

1. Can I change the text on my menus? For example instead of saying applications could I change it to say "Start" (I know, I still can't let go completley, it's like a security blanket :) )

2. When I installed Ubuntu I had the laptop plugged in to mains power. I have unplugged it and now I get told that there is Unknown Time (xx%) Remaining ( the xx is always a real number and does decrease over time). Will this be updated if I let the battery run all the way down or do I have to get down and dirty with some bash jiggery pokery.

3. Everything works, except that whenever I open a window (dont know what Ubuntu calls them so for want of a better word I am talking about any application with a bar accross the top with minimise, maximise and close icons in the top right corner) the text and bar are HUGE, the text looks about 36 point. I am assuming this is a driver issue but everything looks ok in the device manager (but remember I am coming from Windows so any dodgy hardware is always flagged with a nice yellow ! icon.

Many thanks in advance for any assistance with this.

Andy

---

### Post by Paul820 on 2007-11-08
1 - Don't know.
2 - Over time ubuntu will work out how much battery power you have left. At first mine said the same as yours but now it says 2 hours 15 mins. It builds some sort of chart.
3- Just change the size of your font in system->Preferences->Appearance, click the font tab and then change the size of the window title font.

---

### Post by LowSky on 2007-11-08
for #1, what you have to do is just change the icon for the menu, if you right click on a panel you can add new programs and monitors to the panel, one option is a "start" menu that is one column instead of the standard 3. choose that one and deletet the old one. the next thing you will need to do is change the icon, which i am not very sure about. most likely you can edit the program launcher within its properties
I would try it on my computer but I'm stuck at work on a windows machine, and I have a college class tonight. So if you would like I could try to help you in about 9 hours...lol
i gound this, its for debian but it might have some useful information

try this

[http://www.debian.org/doc/manuals/users-guide/ch-mtdyo.en.html#s-alaunchers](http://www.debian.org/doc/manuals/users-guide/ch-mtdyo.en.html#s-alaunchers)

---

### Post by ARhere on 2007-11-08
> **scriptsales said:**
> :)
2. When I installed Ubuntu I had the laptop plugged in to mains power. I have unplugged it and now I get told that there is Unknown Time (xx%) Remaining ( the xx is always a real number and does decrease over time). Will this be updated if I let the battery run all the way down or do I have to get down and dirty with some bash jiggery pokery.


I design Power supplies for my company, many with Lithium Ion and [Lithium Polymer]("http://en.wikipedia.org/wiki/Lithium_polymer") batteries, and I can add that the better the battery, the more of a pain in the **butt** it is to measure it's charge level.

The ideal battery will hold its supply voltage with any load over the entire discharge cycle until it is empty, at which point the voltage sharply drops.  In this idea situation, if the battery voltage does not slowly drop, as in most NiMH or NiCA batteries, then telling you at a glance its charge is hard.  It is because of this most Li battery chargers also have a timer that keeps track of cycle times.

So, yes, fully charging your battery, then letting it run dry while the PC is running will greatly help the efficiency of the power meter.  Make sure you turn off options to shut down the PC when battery level gets low.  Might be bad for Linux to suddenly loose power... <shrug>

-ARhere

---

