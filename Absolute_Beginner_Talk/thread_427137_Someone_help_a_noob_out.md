---
title: "Someone help a noob out"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by riminicat on 2007-04-29
Ok, so I finally kinda understand the xwinwrap thing.  So fare I get that I have to put: 
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet movie.jpg

In the terminal to play the movie, I think.  But I have to replace movie.jpg with the name of the clip I want to play, but how to I enter a path?  This question probably sounds stupid but if I just enter the clip name I don't get anything, so I figured I need to enter the path to get to it, but I don't know how.

---

### Post by Findoo on 2007-04-29
By path do you mean something along the lines of "/home/user/Desktop/file.jpg"?. If so, you would enter
```
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet '/home/user/file.jpg'
``` which would mean the file is within your home folder. Hope that helps.

---

### Post by riminicat on 2007-04-29
thanks it does!!

---

### Post by riminicat on 2007-04-29
ok, so I put this into the terminal:

xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet /home/user/toycom62.mpg

and I got this:

MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2400  @ 1.83GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/user/toycom62.mpg.
File not found: '/home/user/toycom62.mpg'
Failed to open /home/user/toycom62.mpg.


Exiting... (End of file)
mplayer died, exit status 0

What does this mean, sorry, I'm to used to windows but I got sick of it tellimg me I can't do anything cool to my desktop

---

### Post by MyR on 2007-04-29
> **riminicat said:**
> 
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet /home/user/toycom62.mpg

you need to change "user" to your login name

---

### Post by riminicat on 2007-04-29
Hey thanks for the help, I changed that but I'm still getting the same error message

---

### Post by mejy on 2007-04-29
Go into nautilus so that you can see the file, and take  a screenshot of what you see by going to Applications -> Accessories -> Take Screenshot.  That error message means you have mistyped the location to the move file.

---

### Post by riminicat on 2007-04-29
ok

---

### Post by riminicat on 2007-04-29
file:///home/riminicat/Desktop/Screenshot.png
Here is the image, I don't know if this will work

---

### Post by riminicat on 2007-04-29
never mind, I gotta find a place to post it

---

### Post by hyperair on 2007-04-29
Your path is what you see in the Location field when you open the file properties.

---

### Post by Feba on 2007-04-29
Where is the file? Sounds like it's on your desktop, in which case you need to make it user/Desktop/file.thing


Also, "~" will usually fill in for "/home/username/", to save you some time.

---

