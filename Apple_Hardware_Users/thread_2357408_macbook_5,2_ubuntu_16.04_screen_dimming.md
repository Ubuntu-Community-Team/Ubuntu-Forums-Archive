---
title: "macbook 5,2 ubuntu 16.04 screen dimming"
date: 2017-04-01
forum: Apple Hardware Users
---

### Post by warwickben on 2017-04-01
ive been trying for about a month to figure out how to get my keyboard dim controls to dim the screen when i do them nothing happens. i had this working befor i swaped out the old hdd for a ssd and cant not figure out how i got them to work .

every thing i search for tells me about older versions of ubuntu and how to make it work .yes i know a early 2009 laptop is old lol. i mainly use it for surfing the web and arduino. it was free after all. 

graphics = GeForce 9400M/integrated/SSE2
graphics driver nvidia binary version 340.102 from nvidia 340(proprietary tested)

---

### Post by MikeBraxner on 2017-04-02
Without specifics it's difficult to tell. Assuming that your power savings options are properly set, and that your *not* running any inhibiting applications (e.g. vlc), I would suggest to double checking that you actually *can* control the screen brightness via the /sys/class/backlight interface. If you run into trouble there, then [this]("https://ubuntuforums.org/showthread.php?t=2006475&p=12309146#post12309146") might be worth a look. It's a bit dated, but it could at least offer some ideas/pathways.

---

### Post by warwickben on 2017-04-02
theres no files in /sys/class/backlight interface
and i confused what todo with the link you gave me. sorry im still learning linux

---

### Post by MikeBraxner on 2017-04-03
Put simply, if you don't have *any* entries in /sys/class/backlight, then you don't have any way to control your backlight settings whatsoever. I might be wrong about this, but it sounds like there something wonky with your install. 

As a first step, I would suggest booting a fresh, live usb (possibly an alternate disto/release), and check if you can adjust your backlight then/find an interface in /sys/class/backlight. If you do, then it's your install, and you can either try and fix things, or just go for a clean install. If not, ... ah, well ...

---

