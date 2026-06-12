---
title: "Installing on G3 server"
date: 2010-01-15
forum: Apple Hardware Users
---

### Post by dextras13 on 2010-01-15
I have 2 G3 servers with 300MHz processors and a bit over 100mb of ram (I'll probably steal the HDD's and ram from 1 and create 1 slightly better PC). Anyway so I was following [this]("http://ubuntuforums.org/showthread.php?t=405934") tutorial but am already stuck :( I reset the clocks etc via the cmd + option + p + r but then when I tried to boot from the cd I failed. I tried holding down C which took me to a blank screen but I couldn't do anything including trying to get to the terminal. If I did nothing it booted into OSX that is currently installed.

So any ideas. (And since this smilie is awesome I'm gonna add it on) :popcorn:

---

### Post by linuxopjemac on 2010-01-15
did you go into a tty?
> 
Ctrl-option-F1

at prompt type

sudo nano /etc/X11/xorg.conf

Look in the file for the "Modules" Section in there you should have one that says

Load "dri"

change that to

#Load "dri"

Then look towards the bottom of the file for

HorizSync

and

VertRefresh

change the values of these to

HorizSync 58-62

VertRefresh 75-117

Then do ctrl + o then enter

Then do ctrl + x

Then type

sudo killall -HUP gdm

You can also try the alternate-CD option without a GUI installer, I think it's better.

---

### Post by dextras13 on 2010-01-15
I've been told that since the processor isn't intel it won't work. Is that true? What alternate cd option are you talking about?

---

### Post by linuxopjemac on 2010-01-15
you need a PPC version, not an Intel one
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

