---
title: "Dell 720 Printer"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Kamiyay on 2007-10-26
I tried all the other threads. I installed Gusty Gibbon today (new to ubuntu! XD) 

I cannot get my printer to work. The cups log (which I found out where it was from another thread) keeps saying

E [26/Oct/2007:15:57:56 +0000] [Job 16] No %%BoundingBox: comment in header!
E [26/Oct/2007:15:57:56 +0000] PID 5777 (/usr/lib/cups/filter/rastertoz600) stopped with status 127!
E [26/Oct/2007:15:57:59 +0000] [Job 16] Job stopped due to filter errors.

I installed it via this tutorial: [http://ubuntuforums.org/showthread.php?t=215657](http://ubuntuforums.org/showthread.php?t=215657)

I am a student and printing my homework is very important to me. Plz help.

---

### Post by Kamiyay on 2007-10-26
Bumpity Bump Bump

---

### Post by Kamiyay on 2007-10-26
Cmon guys! I got nothing...

---

### Post by Kamiyay on 2007-10-27
I have tried it over and over again to no luck....

---

### Post by Daveth on 2007-10-27
try the backend of this post as a possible solution

[http://ubuntuforums.org/showthread.php?t=591117](http://ubuntuforums.org/showthread.php?t=591117)

---

### Post by Kamiyay on 2007-10-27
Are you refering to the post about removing gnome-cups-manager? If so how do I do that? and how do I install a printer without it?

EDIT:

After uninstalling and reinstalling the printer throught the CUPS web interface, I get a new error:

Starting GPL Ghostscript 8.61... (It is stuck there after the job is stopped)

also I changed the error logging in cups to debug. Here is the error log:

> 
D [27/Oct/2007:10:13:20 -0700] [Job 27] GPL Ghostscript SVN PRE-RELEASE 8.61: DEBUG2: cups_get_matrix(0x809e37c, 0x836eb74)
D [27/Oct/2007:10:13:20 -0700] [Job 27] cups->header.Duplex = 0
D [27/Oct/2007:10:13:20 -0700] [Job 27] cups->page = 1
D [27/Oct/2007:10:13:20 -0700] [Job 27] cupsPPD = 0x8190fc8
D [27/Oct/2007:10:13:20 -0700] [Job 27] cupsPPD->flip_duplex = 0
D [27/Oct/2007:10:13:20 -0700] [Job 27] width = 4800, height = 6258
D [27/Oct/2007:10:13:20 -0700] [Job 27] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [27/Oct/2007:10:13:20 -0700] [Job 27] HWMargins = [ 18.000 36.000 18.000 5.000 ]
D [27/Oct/2007:10:13:20 -0700] [Job 27] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]

It still doesn't work. Anyone got anything else?

Edit: Got it to print. Fixed and SOLVED!

---

### Post by Daveth on 2007-10-28
well done. If you can post how you did it , it might help others out.

---

