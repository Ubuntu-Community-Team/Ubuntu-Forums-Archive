---
title: "How does one rip to FLAC w/ a log file?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-07-26
The flac option does not appear anymore in sound juicer...how can I get it back, and possible get a log of the rip as well to make sure it went ok?

what about using GRIP instead?

---

### Post by FleetAdmiral74 on 2007-07-26
Someone please help, I have tried searching but nothing too useful. Grip just looks way to hard, I cant figure out half the config stuff. And in Juicer, if I try to edit a profile the window just locks up...and I still don't see  a flac option.

---

### Post by cek on 2007-07-26
I can't help with either of these applications, but ripping to FLAC is very easy using ABCDE.  ABCDE can be installed from the synaptec package manager.

Then just insert a CD and from a terminal (go to your music directory first) and:

abcde -o flac -d /dev/cdrom

It will use freedb to tag the tracks and output them to ./Artist_Album/

---

### Post by FleetAdmiral74 on 2007-07-26
Thanks, I will give that a try. I tried looking through the man page...how do I set bitrate? (i want at least 192)

Hmm.....```
ed@database:~$ abcde -o flac -d /dev/cdrom
[ERROR] abcde: flac is not in your path.
[INFO] Define the full path to the executable if it exists on your system.

```

---

### Post by FleetAdmiral74 on 2007-07-27
'nother bump

---

