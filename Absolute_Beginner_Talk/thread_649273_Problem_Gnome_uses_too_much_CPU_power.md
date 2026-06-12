---
title: "Problem: Gnome uses too much CPU power"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by wildnewbie on 2007-12-24
I just installed Ubuntu 7.04 on my 800 Mhz, 512 Ram, with 1.0 gig swap on my box.  I tried Ubuntu 7.10, but it was lagging to the point of unbearable.  This is my first attempt of seriously using Linux, Ubuntu in particular since I heard lot of positive comments about.  Here is what I have done and learn about Linux on my system.

1. Installed Ubuntu 7.10, Everything is lagging.  Boot into color stripes after installing GStreamer and Flash plug in for firefox, I was trying to watch flash video on youtube.com

2. Installed XUbuntu 7.10, When starting terminal I was log out and have to log in again, after a couple of times, Screen turn into color stripes,

I made a post, some suggested using Puppy Linux, Ubuntu 7.04  and other distributions

3. Tried Puppy Linux Live CD, very satisfied with performance of system, but graphic is horrible.  Max. bit on my Intel 810 is 24 bit, it was displaying 16 bit.

4.  (current) Installed Ubuntu 7.04, installed GStreamer package, sound works great, play .mp3 from NTSF (window) partion OK.  Dare not to install flash, cause system might crash.  Here are a list of problems I am currently have.

      i.  When, I am not doing anything.  I mean no program is running. I am not sure how it works on Ubuntu, but as far as I know, I closed all programs I open in Ubuntu.  GNOME IS USING 15-40% OF CPU. AND BY 15-40% I MEAN, IT FLUCTUATING BETWEEN 15% TO 40%, WELL IT'S MORE LIKE 15%, 40%, 15%, 40%.  
THIS IS A PIC [[IMG]http://img529.imageshack.us/img529/7648/unstableyc9.th.png[/IMG]](http://img529.imageshack.us/my.php?image=unstableyc9.png)

     ii.  FIREFOX IS LAGGING, IT TAKES ABOUT 4 SECONDS TO FINISH LOADING YAHOO.COM, I believe GNOME is using 100% of CPU, when firefox is staring.

    iii.  EVERYTHING ELSE IS SLOW BECAUSE GNOME IS USING TOO MUCH CPU POWER.

THAT'S ALL I KNOW ABOUT THE PROBLEM I AM HAVING WITH UBUNTU 7.04 NOW.

ALL OF THESE PROBLEM COULD BE CAUSED FROM MY GRAPHIC CARD (INTEL 810).

---

### Post by Rocket2DMn on 2007-12-24
In a terminal you can "top" to see what is using up the CPU so much, or just sort the gnome system monitor processes by CPU usage to get more details.  Are you using compiz-fusion or other fancy graphics?  If so, disable it and use the basic Metacity window manager.
DId you install the drivers for i810?
edit: see [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b26796d178114bd3fdea5600480d8ab3137274d1](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b26796d178114bd3fdea5600480d8ab3137274d1)

---

### Post by LaRoza on 2007-12-24
You might prefer Xfce instead of GNOME.

---

