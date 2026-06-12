---
title: "problems with ubuntu 5.10 DVD"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by sephiroth99 on 2006-05-24
Hi! First post here!

I downloaded Ubuntu 5.10 DVD, version amd64. I wanted to try it out with the liveDVD and install it if it works, but it doesn't... When I try to use the liveDVD function, everything goes well until it starts the Xserver windows, right after the ubuntu logo with the scrolling list with OK on the right.

The error I get is something like "no devices detected" and "cannot initalize xserver, no screen found". If someone knows a way to dump the log, I could put it here.

my specs are :

opteron 165
1gig ocz platinium
dfi lanpartyUT nf4 ultra-d
sapphire radeon x800gto2 pci-e (16 pipes unlocked)

I tried it on another amd64 comp, and everything works well.

someone have an idea? because ubuntu looks great....:(

---

### Post by uteck on 2006-05-24
Reboot with the DVD in, but do not press enter.  Use the various 'F' keys to see the different boot options.  You probibly need to pass an option so X starts up properly.  
But You will have better luck with a Dapper since it will be released next week.

---

### Post by sephiroth99 on 2006-06-02
hi, its me again,

just downloaded the new version (6.10) and if I try to start the livedvd, it is doing the same thing. on the other hand, when I choose the safe graphics boot mode, at the same place where it would crash, my monitor shuts down and I can hear the boot tune of ubuntu...

It is doing the same thing if, after xwindow crashed, I change some settings in /etc/X11/xorg.conf in the console that pops up. if I change the driver from "ati" to vesa, and I type "startx" at the console, the monitor shuts down and I hear the boot song of ubuntu

I found some help in this thread : [here]("http://www.ubuntuforums.org/showthread.php?t=184517&highlight=ati+x800")

anyone have some clues?

---

