---
title: "Garbled display - wrong monitor driver installed"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Ken101 on 2007-11-19
I'm using 7.10 with a new Samsung 794v CRT monitor.
Ubuntu detected a "generic monitor" and set resolution to 600x800 with a low refresh rate.
I changed the monitor properties to a similar Samsung moder but now when I restarted the display can't be read at all.
I can start in safe mode but do not do not know how to proceed from here.
Any help appreciated.
Thanks

---

### Post by skymera on 2007-11-19
try:

sudo dpkg-reconfigure -phigh xserver-xorg

then select your desired resoultions :)

also what is your graphics card?

---

### Post by Ken101 on 2007-11-19
Thx for quick reply.
OK, I got my display back by using the command.
Now, how do I get to to a resolution of 1024x768 with 85Hz
I'm using a Foxconn m/b P4M8907MB-RS2H with onboard graphics, I think Unichrome.

---

