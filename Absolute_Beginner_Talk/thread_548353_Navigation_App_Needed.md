---
title: "Navigation App Needed"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Jabulani on 2007-09-11
Hi - Wow I really am enjoying Ubuntu! I built a small form factor PC that runs off 12v for my sailboat, and since having all kinds of XP issues, swithced to Ubuntu. It is by far more stable, more user friendly! \\:D/

One piece of software I am trying to replace is my Fugawi navigation software. It uses free navigation charts, (raster and vector charts from NOAA), and takes a GPS signal to plot your position in real time on the screen. There is also a freeware navigation app called Sea Clear, that runs on Windows, and reported does well on WINE.

My question to this esteemed forum is:

a) is there a Ubuntu compatible navigation app available?
b) if not, what is the recomendation regarding WINE ([http://www.winehq.org/](http://www.winehq.org/)) and can it run on Ubuntu?

thanks and have a great day.

---

### Post by ijason on 2007-09-11
wine can definitely run on ubuntu, from what other people have told me. i've gotten the program to install, but have never managed to actually run anything with it! the syntax for using wine - if that's what you're asking - is to simply install the package. then when you want to install a windows program you right-click on the executable and choose to 'run with another program' and choose Wine. which should be listed as an option.

after the install you will either need to right-click on the executable and do the same thing each time, or make a link that runs it command-line 'wine navprogram.exe'. one tricky thing about wine is that it installs the programs into a hidden directory in your home folder called .wine                     once you get into .wine you can see the directory tree is pretty logical.

another program that was recommended to me was CrossOver. it's actually the purchasable program by the same people who make WINE. it runs photoshop for me when wine couldn't. they have a big list of the compatible applications on their website. just do a google search. 

/good luck!

---

