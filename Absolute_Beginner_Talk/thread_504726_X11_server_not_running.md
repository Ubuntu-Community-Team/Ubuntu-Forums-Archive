---
title: "X11 server not running ??"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by djekels on 2007-07-19
Ok I am stumped.

I see there is a X11 server running on my newly installed ubunto 7.04
I open a temrinal and run xhost + on my laptop

I ssh into one of our production Linux hosts; set my DISPLAY variable and try to run a X11 app.

I get the following.
/usr/bin/X11/xdpyinfo:  unable to open display "djlenovo:0.0".

env | grep DISPLAY
DISPLAY=djlenovo:0.0

Does anytone know how to get past this point?

---

### Post by steve.horsley on 2007-07-19
I think you have to tinker with a config file before it will even listen for incoming connections - this is in addition to xhost +.  xhost only controls the authorisation.

If it works (It should if the server is Linux, not sure about other unix systems), it is easier just to use:
**ssh -X servername**
which sets up tunneling ov X over SSH so you can launch your X apps without manually configuring DISPLAY etc. e.g. 

**ssh -X -C servername **
might be quicker over WAN links because it also enables compression.

---

