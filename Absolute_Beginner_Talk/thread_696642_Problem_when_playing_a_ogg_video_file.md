---
title: "Problem when playing a ogg video file"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-14
i have a Problem when playing a ogg video file. when i start the video it opens and quits before playing.Please help me

---

### Post by jan quark on 2008-02-14
which palyer do you use?

try to load the player via the terminal and post any error messages 

thank you

---

### Post by kaiju on 2008-02-14
if there are no better bets, perhaps try running the movie player from a terminal, to get some feedback on what the problem could be.

---

### Post by adi_das on 2008-02-14
> 
** (totem:10150): WARNING **: Error connecting to D-Bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (totem:10150): WARNING **: Failed to connect to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(totem:10150): GStreamer-CRITICAL **: gst_value_set_fraction: assertion `denominator != 0' failed

** (totem:10150): CRITICAL **: gst_video_calculate_display_ratio: assertion `num > 0' failed
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 70 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


This is the error when playing the file in totem player via terminal

---

### Post by kaiju on 2008-02-14
wow. the thing is i never use totem... besides, i don't think d-bus has anything to do with media formats. hope someone here knows more about this though.

i say you should try mplayer or vlc because they both play pretty much anything that's around.

---

