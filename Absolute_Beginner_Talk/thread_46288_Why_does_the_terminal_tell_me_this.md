---
title: "Why does the terminal tell me this?"
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by kolya on 2005-07-04
Hi, this doesn't actually cause me any problems but I am wondering why the terminal tells me this sometimes when I type in commands.

kolya@pipeline:~$ sudo gedit
- using device default
- using device default
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
kolya@pipeline:~$

Thanks for all the info.  It is appreciated.

---

### Post by SteExp on 2005-07-04
Probably your Audio board is not supported to sistem...

but... i'm not sure

---

### Post by kblood on 2006-02-24
Hi, I have the same, and I was wondering why as well.

I have a Sony Vaio VGN-FS315M, with the HDA Intel sound card. It seems to be related to the features of the card, and eventually finds a sound option that works.

What I wonder is why the first one fails (44.1Khz, stereo, 16bit), which is fairly standard.

---

