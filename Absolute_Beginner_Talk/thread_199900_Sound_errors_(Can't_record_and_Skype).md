---
title: "Sound errors (Can't record and Skype)"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Sitix on 2006-06-19
When I open Audacity it gives the following errors in the terminal, I am not able to record or to play music in there. There are several programs that DO work with the music (XMMS, amaroK..) and others that don't work (Audacity, Skype).

Now I got it to work so the other one can talk to me without it giving an error but that is not what I want, I wanna talk back! :P

The errors:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Can someone help me?

---

### Post by cacharreo on 2006-06-19
Try using
***gstreamer-properties***
I fixed a similar problem changing the defaults setting8-)

---

### Post by Sitix on 2006-06-19
Just for example, if I change it to ALSA I get:
ALSA - Advanced Linux Sound Architecture: Could not establish connection to sound server

If I change it to OSS:
OSS - Open Sound System: Could not open resource for writing.

But when it starts I get:

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'


So I tried installing them using apt-get but that didn't work either.

When I do ALSA, I get this in the terminal:

gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for writing. [gstalsasink.c(833): gst_alsasink_open (): /pipeline0/alsasink1:

But that makes no sense because I installed alsa... I really don't have a clue what it might be?

Edit: I reinstalled all the ALSA packages, but no results. Still the same errors.

---

