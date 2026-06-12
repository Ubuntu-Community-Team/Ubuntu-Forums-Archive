---
title: "xwinwrap help, no other suggestions worked"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by riminicat on 2007-04-29
Ok, so I ran this code in the terminal, and I got these results, any help?

MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2400  @ 1.83GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing movie.mpg.
File not found: 'movie.mpg'
Failed to open movie.mpg.


Exiting... (End of file)
mplayer died, exit status 0

---

### Post by riminicat on 2007-04-29
any one?

---

### Post by mcduck on 2007-04-29
Umm. Could you post the command you tried to run?

Anyway, looks like you tried to open a file called 'movie.mpg' which either doesn't exist, or then you are not in the same directory when running the command. Check the file name and try using full path to the file.

---

### Post by riminicat on 2007-04-29
Sorry, I didin't relize the command didn't paste:  xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet movie.mpg

---

### Post by riminicat on 2007-04-29
from what I understand the command is supposed to display what ever is in mplayer as the desktop wall paper

---

### Post by Najand on 2007-04-29
The error means the file doesn't exist. Did you try with the full path of the file?

---

### Post by mcduck on 2007-04-29
> **riminicat said:**
> Sorry, I didin't relize the command didn't paste:  xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet movie.mpg

You should replace the 'movie.mpg' with a full path to some movie file you actually have on your computer.

---

### Post by riminicat on 2007-04-29
Hey thanks, if I have a dvd iso, do you think it will play a video from that?

---

### Post by Najand on 2007-04-29
VLCplayer can open ISO files and it canshow them on as the desktop... Maybe you should give it a try.

---

### Post by riminicat on 2007-04-29
sweet!! Thanks for helping a noob, I was the "expert" at school with Windows, it feels weird not knowing how to get things working

---

### Post by riminicat on 2007-04-29
Thanks I like it

---

