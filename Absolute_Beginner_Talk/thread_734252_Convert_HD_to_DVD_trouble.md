---
title: "Convert HD to DVD trouble"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by crackatoe on 2008-03-24
I just tried using K3B to convert my first HD video to DVD (720 x 480) ntsc.  It's a 720p, h.264 stream clip in a .mov file. 

Everything looks correct, but the playback will jerk every second, as if it's catching up. It doesn't' seem to lose sync sound, other than the instant of lag (which wouldn't be noticeable if it didn't happen ever second).. 

With no previous HD experience, I'm asking the rest of you if this is a typical result of downcoverting? 

With digital formats being very specific, I thought that going from High to Standard definition would be just a matter of number crunching, but apparently there's still some voodoo in it. 

Any suggestions?  Thank you.

---

### Post by chewearn on 2008-03-25
Sounds like a frame rate conversion problem.  What application do you use to convert the HD to SD?  I don't think K3B is doing capable of video format conversion.

---

### Post by crackatoe on 2008-03-25
There is an advanced menu for choosing the type of video source, and the type of video output. I selected h.264 as input, and the DVD res of 720 x 480 as output. I didn't try to get fancy.

---

### Post by chewearn on 2008-03-25
I can't find what you are talking about.  Sorry, I can't give you more help.

---

### Post by crackatoe on 2008-03-26
Thank you for your suggestion on the frame rate. I've tried another application, Avidemux, which has some mp4 support. Unfortuneately, the DVD played as if it were half-speed.  I'm not sure what that means, but the different result is encouraging. Perhaps I am only a couple of tweak away. :)

---

### Post by chewearn on 2008-03-26
If you are planning to convert video frequently, it might be worth it to consider learning command line mplayer (or another command line tool, e.g. mencoder).  It will allow you to automate the process by a script, rather than having to click on the GUI for every video.

Unfortunately, I have not done this before; I have only read some howtos in the forum.

EDIT:  Here is some help:
[https://help.ubuntu.com/community/MEncoder](https://help.ubuntu.com/community/MEncoder)

---

