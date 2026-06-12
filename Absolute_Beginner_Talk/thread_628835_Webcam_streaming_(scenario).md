---
title: "Webcam streaming (scenario) ?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-12-01
I do not have a webcam, but was just thinking this, so please bear with me.
I have never owned one either, so all of this is just thought, thus far.

If I were to go out and buy me a brandnew webcam, could I somehow stream it live over my network so any system in the house could view the webcam, just by connecting to it ?

If so, how would I go about doing this ?

---

### Post by jordank on 2007-12-01
trying to set up some home security?

---

### Post by Dr Small on 2007-12-01
> **jordank said:**
> trying to set up some home security?
Yeah, that is my basic idea. I was just wondering if I could do it.

---

### Post by jordank on 2007-12-01
I'm actually trying to do something similar, but i cant find any decent webcam programs.

I downloaded something from synaptics called motion, which is supposed to be a motion detector, but i don't know where it goes when i download it.  Happens with a ******** of my programs too. I get them from synaptics, and just cant find them.

---

### Post by Dr Small on 2007-12-01
Try typing 'motion' in the terminal.

---

### Post by doc_holiday on 2007-12-05
I'm looking for the same thing. Any suggestions on good software to do this?

---

### Post by johnnybirdman on 2007-12-07
> **doc_holiday said:**
> I'm looking for the same thing. Any suggestions on good software to do this?

Guess we are all looking for the same thing.  I just got a logitech orbit MP today.  I have been reading the motion wiki and although I like the command line for some things, that program might be a bit technical for me, but I'm going to try anyway.  If anyone comes across anything different let us know.

J.

---

### Post by rafalr on 2007-12-18
Hi,

It is not that difficult. I wasted yesterday 2 hrs to get me webcam working, and only ca 1 hour to install, configure and finetune the motion settings.

Basically:
- before you install motion make sure to have ffmpeg + lavcodecs installed
- after you install motion from repos/synaptic (just regular installation), locate the motion.conf file (in Edgy this is located in /etc/motion; could as well be in /usr/local/etc).

whatever you want motion to do, or want to change any settings this is being done in that file. The original file will contain default settings which may (or may not) be sufficient to have it running, but you may want to take a look at some basic tuning, like:
width (of picture/movie = > this should be according to your webcam specs)
height
framerate (of you video = > this should be according to your webcam specs)
quality (of the jpegs used to build your video)
etc

As you see, it is no magic - just very normal settings you would want to put in any video file.

Take a look at:
[http://www.lavrsen.dk/twiki/bin/view/Motion](http://www.lavrsen.dk/twiki/bin/view/Motion)
enything you need to know is there

Cheers,
rafal

---

### Post by johnnybirdman on 2007-12-18
> **rafalr said:**
> Hi,

It is not that difficult. I wasted yesterday 2 hrs to get me webcam working, and only ca 1 hour to install, configure and finetune the motion settings.

Basically:
- before you install motion make sure to have ffmpeg + lavcodecs installed
- after you install motion from repos/synaptic (just regular installation), locate the motion.conf file (in Edgy this is located in /etc/motion; could as well be in /usr/local/etc).

whatever you want motion to do, or want to change any settings this is being done in that file. The original file will contain default settings which may (or may not) be sufficient to have it running, but you may want to take a look at some basic tuning, like:
width (of picture/movie = > this should be according to your webcam specs)
height
framerate (of you video = > this should be according to your webcam specs)
quality (of the jpegs used to build your video)
etc

As you see, it is no magic - just very normal settings you would want to put in any video file.

Take a look at:
[http://www.lavrsen.dk/twiki/bin/view/Motion](http://www.lavrsen.dk/twiki/bin/view/Motion)
enything you need to know is there

Cheers,
rafal


Sounds great, now if I could only get my logitech orbit MP to work.... at all....

---

### Post by Dr Small on 2008-02-07
So what would be a good cheap webcam, that works out of the box?

---

