---
title: "Totem Player crashes MP3s, after Feisty upgrade"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by futuroimperfetto on 2007-04-21
Hello everyone,

this is my first shy post. I have been using Edgy Eft for 6 months with almost no need for maintenance, and yesterday I updated to Feisty Fawn.

Everything seems to work correctly, but the Totem player breaks each time try to open an MP3.

If I lanuch totem from a terminal and then try to open an MP3, the program closes instantly and I get the following writing in my terminal:

  received X error event: BadMatch (invalid parameter attributes)
  The program 'totem' received an X Window System error.
  This probably reflects a bug in the program.
  The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 84 error_code 8 request_code 141 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I dot know if this is of help: yesterday I made a mistake and I removed my newly installed ATI drivers (through the restricted drivers' manager). The X window system would not want to work when I rebooted, so I have installed the drivers again and now everything works, except Totem.

Thank you everyone

-Francesco

---

### Post by johanPO on 2007-04-25
I have the same problem. Other programs like mplayer and kaffeine are working. So that's the easy solution, but I would like to see this fixed as it was working in 6.10

---

### Post by futuroimperfetto on 2007-04-29
Thanks for the reply. 

Yeah, I've looked around and I could not find a fix in the forums. I've seen that other players work, but I would want to see a fix for this.

I do not understand too much what the relationship between totem-xine and totem-gstreamer is, but the second one does not crash while playing mp3s, so I've switched to the second temporarily.

Another (possibly unrelated) problem I'm having with totem-xine and various other players is that they have color issues: blue colors are inverted with red when playing .avi files. There are several other threads on this, but I thought I should mention it nonetheless (I have an ATI Mobilty X1600 graphic card).

Cheers

---

