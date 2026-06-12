---
title: "[SOLVED] Combining AVI files together??"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-25
Is there a GUI based application that will allow me to join together AVI files that have the same resolution/frame rate/audio and video bitrates together?

---

### Post by PilotJLR on 2007-08-25
I don't know a GUI app, but avimerge is an excellent, and easy to use command line tool to do this.

---

### Post by chrome307 on 2007-08-25
Sounds good ............ where can I find it?

I found some instructions here on the usage ...... do you anywhere else?

[http://www.transcoding.org/cgi-bin/transcode?Avimerge](http://www.transcoding.org/cgi-bin/transcode?Avimerge)

---

### Post by serfcx on 2007-08-25
to combine avi
cat 1.avi 2.avi > 3.avi
Then
mencoder -noidx -ovc copy -oac copy -o output.avi 3.avi

this will clear up any video/audio synch problems

To make a dvd from the avi see tovid
[http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

---

### Post by chrome307 on 2007-08-25
Do I just do this using the TERMINAL?

---

### Post by serfcx on 2007-08-25
> **chrome307 said:**
> Do I just do this using the TERMINAL?

yep !

---

### Post by ToySouljah on 2007-12-16
I know this is an old thread, but I've been using Ubuntu now for about 7 months and quit Windows cold turkey, but I have to say....the transcode thing actually seems a lot easier and quicker than any program I used in Windows...lol.  Worked like a charm the first time around  :)

---

### Post by orionvc on 2007-12-23
Yup, slowly but surely taking away tasks from my Windows box too. Very cool!

---

