---
title: "Jack server problem"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by tordan on 2007-01-16
I am trying to use a looping program and have been attempting to try Sooperlooper, Jackbeat, and klupe. However, when I open any of these programs it keeps saying that it is unable to connect to the "Jack server" or something.
What is this? What should I do?

---

### Post by kevindubrow on 2007-08-09
I am having the same problem. I just installed Ubuntu Studio and many of the audio programs (the reasons I got Ubuntu Studio) will not run because of issues with Jack. I am not the most advanced Linux user and I don't know Jack :) so hopefully someone can help me get all of my programs running. Any help would be great!

---

### Post by tupesadilla on 2007-08-25
For any of these programs to work, you need to have the jack server running. to do this, for one make sure jack is installed. open up the jackcontrol (via command line or via applications>sound and video>JackControl) then when it opens click start on the box and it will tell u jack server is running, then when opening those programs you shouldnt have any problems

---

### Post by Nidding on 2008-02-21
> **tupesadilla said:**
> For any of these programs to work, you need to have the jack server running. to do this, for one make sure jack is installed. open up the jackcontrol (via command line or via applications>sound and video>JackControl) then when it opens click start on the box and it will tell u jack server is running, then when opening those programs you shouldnt have any problems

I've tried that. It runs for a few sec, then it stops. Any ideas what could be wrong?

---

### Post by AtlasDark on 2008-02-21
Does it give a specific message or inform you if it's already in use? I use Ardour in conjunction with cqjack (or something of the like, can't remember specifically), which provides diagnostic messages for selective failures.

---

### Post by Nidding on 2008-02-21
I tried a few things. When I tick the "Realtime" box in setup, it stops just a few secs after I start it.
The message console gives me the following
> **"Message console"]
23:33:52.307 Patchbay deactivated.
23:33:52.346 Statistics reset.
JACK tmpdir identified as [/dev/shm]
23:33:52.478 MIDI connection graph change.
23:33:52.615 MIDI connection change.
23:34:00.641 Startup script...
23:34:00.642 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/nidding/.kde/socket-nidding.
23:34:01.111 Startup script terminated with exit status=256.
23:34:01.114 JACK is starting...
23:34:01.117 /usr/bin/jackd -R -dalsa -dhw:0 -r48000 -p1024 -n2
23:34:01.129 JACK was started with PID=6240 (0x1860).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions said:**
> 
23:34:05.229 XRUN callback (47 skipped).
jackd watchdog: timeout - killing jackd
zombified - calling shutdown handler
23:34:07.211 Shutdown notification.
23:34:07.215 Client deactivated.
23:34:07.220 JACK was stopped successfully.
23:34:07.224 Post-shutdown script...
23:34:07.225 killall jackd
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
jackd: no process killed
23:34:07.487 Post-shutdown script terminated with exit status=256.

If I untick "realtime, the messages keeps saying 
"XRUN callback (46 skipped)" every 1½ sec or something like that. It doesn't stop by itself, but I can't get any sound through.

By the way, I just installed Studio Ubuntu. Shouldn't it be able to run real time?

---

### Post by Nidding on 2008-02-22
I got it to work. It turns out that it was due to some problems with the onboard sound card. I switched that off in the bios, and now it's working fine.

---

