---
title: "Ubuntu Horribly Slow!"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by BodaciousBrian on 2007-12-14
I'm running ubuntu 7.10, with gnome.

to open firefox to post here, it took at least 60 seconds.  To open system monitor it took about 30.  System monitor says my cpu is about 3% in use, but when i clock different tabs in it, it takes 7 seconds to make the switch, the window turns grey, and my mouse begins to lag.  half of my swap is used..  I have  nothing running other than firefox and system monitor. and my typing here sometimes falls 2-3 words behind me!

This all started yesterday when i was playing in counter-strike under wine, the game froze, and reset.  i came back on and the clock disapeard off od the gnome top bar.

I'm really not up for a resinstall, but that is the only way i know how to fix this!

---

### Post by thelatinist on 2007-12-14
Perhaps your swap is not mounting?  I had that problem once when I had to do a hard reset.  I finally fixed it by reformatting my swap partition in GParted.

---

### Post by siciliancasanova on 2007-12-14
Yeah try restarting your machine normally and then check to see if your swap is mounted.

For example, if you have a dual boot set up and you just do a hard power off your Windows partition most likely will not mount.

---

### Post by BodaciousBrian on 2007-12-15
Ok i reformatted my swap partition with gparted.  It doesnt show that it is mounted anywhere but i dont think its supposed to...

After a restart my computer slows down exponentially..  I was just playing counter-strike in wine.  ANd my frame rate started at 75ish, and worked its way down to the teens, then quickly to a couple fps, and then i got 1 frame in 30 seconds before i just hit the power button(Num lock wouldn't work at this point!).

Its almost like my swap isn't clearing itself or something!, and once its full, it quickly dies.

and what is trackerd in processes? currintly taking 40% of my cpu.

---

### Post by timbounceback on 2007-12-15
I think trackerd is the indexing daemon for the search tool included w/ Ubuntu called Tracker. It is busy indexing your computer, and this is what is probably taking up all the resources. :)

Tim

---

### Post by BodaciousBrian on 2007-12-15
ok i looked at system monitor again, my swap was off after restarting and my used ram as steadily climbing, until i closed trackerd..  after killing that app, and turning the swap on, everything is running fine..  How do i set my swap to turn on at boot?

---

### Post by BodaciousBrian on 2007-12-15
to fix this problem:

sudo apt-get remove tracker

---

