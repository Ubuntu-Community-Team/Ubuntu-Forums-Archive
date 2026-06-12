---
title: "Jack and Hydrogen"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-06-07
What is the Jack server and how do I use it? Many of the Ubuntu Studio apps require it. I found a website, but no documentation.

Hydrogen exports the song as MIDI only. Is there a similar drum machine that exports MP3 or other file type? Or, how can I use these Hydrogen MIDI files with Audacity or GNUSound?

Thanks

---

### Post by whizbaby on 2007-06-07
the package name is

jackd

its like a big software patch bay. Just run

jackd &

from console (after installing jackd of course)
and report the error messages here ;)

---

### Post by RichPicker on 2007-06-07
I get no error messages in the terminal when I start jackd or jackd &

But I get this from Jack Control

10:34:40.565 Could not connect to JACK server as client. Please check the messages window for more info.

---

### Post by whizbaby on 2007-06-07
> **RichPicker said:**
> I Please check the messages window for more info.
And, did you?

---

### Post by RichPicker on 2007-06-07
Yes. But I don't understand what it's telling me. I see that something's wrong, but I don't know what it is. 
Here it is.

10:46:14.498 Patchbay deactivated.
10:46:14.529 Statistics reset.
10:46:14.562 MIDI connection graph change.
10:46:14.750 MIDI connection change.
10:46:33.027 MIDI connection graph change.
10:46:35.095 MIDI connection graph change.
10:46:36.604 Startup script...
10:46:36.604 artsshell -q terminate
can't create mcop directory
Creating link /home/rich/.kde/socket-rich-laptop.
10:46:36.877 Startup script terminated with exit status=256.
10:46:36.877 JACK is starting...
10:46:36.877 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
10:46:36.891 JACK was started with PID=9901 (0x26ad).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
10:46:36.895 JACK was stopped successfully.
10:46:36.895 Post-shutdown script...
10:46:36.895 killall jackd
jackd: no process killed
10:46:37.104 Post-shutdown script terminated with exit status=256.
10:46:38.998 Could not connect to JACK server as client. Please check the messages window for more info.

---

### Post by RichPicker on 2007-06-07
I found the directions for setting up Ub Studio. 
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

I am now here:
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

But I get zero results when trying to open QjackCtl

---

### Post by RichPicker on 2007-06-07
Got jack control open. The documentation was incorrect 
qjackctl is all lowercase.

---

### Post by whizbaby on 2007-06-07
> the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
any sound app runnin?

---

### Post by whizbaby on 2007-06-07
> **RichPicker said:**
> Got jack control open. The documentation was incorrect 
qjackctl is all lowercase.

rofl

---

### Post by shen-an-doah on 2007-06-07
> **RichPicker said:**
> Hydrogen exports the song as MIDI only. Is there a similar drum machine that exports MP3 or other file type? Or, how can I use these Hydrogen MIDI files with Audacity or GNUSound?

Thanks

Hydrogen will export songs as .wav files. Just go File > Export song, then hit browse, select where you want to save the file, type in a filename (<yoursong>.wav), hit OK and then hit Export.

---

### Post by RichPicker on 2007-06-07
Yeah, me too.

I've got the 3 apps open: jack control, VkeyBd, and ZynAddSubFX.

No Clients are listed in the Connections window under: 

AUDIO
Readable Clients/Output Ports  or  Writable Clients/Input Ports

---

### Post by RichPicker on 2007-06-07
If it's dependent on my correctly setting the options in Jack Control>Set Up via trial-and-error, this will take some time.

---

