---
title: "Brand new to Linux"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by aznmodder on 2006-01-14
well my friend told me to try it out so i did...it looks very nice and everything is stable so far....only issue i have is my wacom pad is acting very funky...the mouse works but it acts like it's the pen

i did a search feature around the forums but im totally new to linux and the terminal>me but hopefully ill figure it out with some time...if u have any recommendations please note them or some link to a good read for beginners

im doing the automatix right now to get alot of the common programs/plugins

edit: resolution looksa  little funky too but its alright i think

---

### Post by drfalkor on 2006-01-14
Hello guy,.. you are new to linux ? you should read this then: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

-And remember, Linux is not windows :D

---

### Post by matthew on 2006-01-14
Welcome. If you run into problems or have questions these forums are the place to ask. The people here are pretty cool and can usually help.

---

### Post by Azion on 2006-01-14
There's always great help or on the IRC server.
Read through the Wiki, it'll give you a better insight into things

---

### Post by aznmodder on 2006-01-14
alright just a few things

[[IMG]http://img499.imageshack.us/img499/1052/screenshot3lm.png[/IMG]](http://imageshack.us)

^^^ i cant seem to access sda1...its probably for a really nooby reason but could someone explain

i just use automatix or whatever to isntall most of the things i need so that firefox install isnt gonna matter but i dont really get how to do the linuxwacom driver thing...i was reading the guide:

[http://www.ubuntuforums.org/showthread.php?t=25151&highlight=wacom](http://www.ubuntuforums.org/showthread.php?t=25151&highlight=wacom)
[https://wiki.ubuntu.com/WacomTabletIssue](https://wiki.ubuntu.com/WacomTabletIssue)

i mean i dont really know where to start because the wacom pad works...just not right...the mouse acts like the pen so i assume i should just install the drivers:

copy/move the wacom.c from there to drivers/usb/input in your
linux-source-driectory

where is the linux source directory?

edit: and just for giggles...middle click doesnt close tabs in firefox ; P

---

### Post by steve.horsley on 2006-01-15
[QUOTE=aznmodder]
^^^ i cant seem to access sda1...its probably for a really nooby reason but could someone explain[/QUOTE]
I wonder if anything is mounted there at all. Can you post the output from the command-line commands **df** and **mount?**
[QUOTE=aznmodder]
edit: and just for giggles...middle click doesnt close tabs in firefox ; P[/QUOTE]
That old chestnut. Type in the URL about:config, filter on **middle**,  and set middlemouse.contentLoadURL to False by double-clicking it.

Can't help you about compiling your wacom drivers, sorry.

---

