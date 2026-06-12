---
title: "Startup script"
date: 2012-05-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by manjack92 on 2012-05-06
Hey i had a mouse problem in ubuntu(i think it was 10.11/0 or something similar to that) last i try'ed it so i switched to win 8 mean time, i heard that GDK_NATIVE_WINDOWS=1 fixes it (which  i did try and it does) but is there away to set it that way it runs on startup? and also i don't know how to put it in like script unless there's some other codes that i am missing :confused: since i am kinda new to linux /Ubuntu  i also try'ed it in opensuse and same problem so that's 2 systems down at least i wanna try to get it to work in this one :-$ info on mice to catch - it's a Logitech one

[http://www.logitech.com/en-us/mice-pointers/mice/devices/6383](http://www.logitech.com/en-us/mice-pointers/mice/devices/6383)
(similar - i think it's that one gotta ask the person who gave me it)

also if there's a thread on this that i couldn't find i would like  a link

---

### Post by papibe on 2012-05-07
Hi manjack92. Welcome to the forums!

You have 2 options:

1. For personal use (just your user) add this line to your ~/.bashrc
```
export GDK_NATIVE_WINDOWS=1
```

2. For system-wide, add this line to your /etc/environment
```
GDK_NATIVE_WINDOWS=1
```

Then restart your machine.

If you want to read more about this, take a look at this [tutorial]("https://help.ubuntu.com/community/EnvironmentVariables"). Specially the section called 'Persistent environment variables'.


I hope that helps, and tell us how it goes.
Regards.

---

### Post by manjack92 on 2012-05-07
Sadly my G74sx is having problems getting on linux live cd's(with -r cds) atm so until i can get a proper dvd/rw/usb(which i am going to get now) then i will save that ..i guess this is what happen's to newer computers/laptop's if it weren't because of my liking for linux systems then i would not bother with it :evil: also 1 extra system down - mint 12 mouse doesn't work/right click  on it - so in total 3 are useless to me unless a fix comes out and the only TEMP fix is that one that i have to put and for me to put it i'd have to have the extra time i don't have (time until mouse right click fails which then following the keyboard fails).

my mistake + Forgot to thank papibe + THANKS!:KS

TO Papibe - i logged in normally then the mouse stopped working /left and right click / so i couldn't do much apart from restart / log off\
update - update - all i had to do was disable my touchpad ...so much for the little things  

so if your on a G74SX and having problems with mice (specifically this one [http://www.logitech.com/en-us/mice-pointers/mice/devices/6383](http://www.logitech.com/en-us/mice-pointers/mice/devices/6383)) ..disable the touch pad

---

