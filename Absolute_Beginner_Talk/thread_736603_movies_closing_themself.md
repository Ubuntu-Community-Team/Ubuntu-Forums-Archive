---
title: "movies closing themself"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by naits1986 on 2008-03-26
Hello! I have a problem, I cant watch any movies, they just close themself when I try to open them..
I ran a ''free'' command and this is the output:
$ free
             total       used       free     shared    buffers     cached
Mem:       2062236    1754756     307480          0      88028    1067724
-/+ buffers/cache:     599004    1463232
Swap:      2048276          0    2048276

And this with only the terminal and mozilla running..

Please dont tell me to get a different graphics driver, I have finally got the desktop effects to work with ati radeon mobility x1800:)

Anyone got an idea of what to to??

---

### Post by sumguy231 on 2008-03-26
Assuming you're using Totem (the default video player) to play them, I would suggest you go to the directory with your movies in them (Use cd /path/to/movies/goes/here) and the run 'totem <name of movie file>' and see what error output you get.

---

### Post by naits1986 on 2008-03-26
$ totem cic-sa66.avi 
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 54 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
 
Here it is:)

---

### Post by naits1986 on 2008-03-26
But I tried it in vlc to.. here the msg from that one:

$ vlc cic-sa66.avi 
VLC media player 0.8.6c Janus
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Value in failed request:  0x3600006
  Serial number of failed request:  85
  Current serial number in output stream:  86

---

### Post by Vadi on 2008-03-26
Does it happen with all movies, or just this one?

---

### Post by naits1986 on 2008-03-26
It happens with all movies.. I think it has something to do with the RAM, but I dont know, as I am noob:)

---

