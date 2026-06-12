---
title: "How to send a fax"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Dafydd on 2006-11-29
Hi
Anyone know how to send a fax?


I normally just use nm-applet and select a wireless but my machine (Sony Vaio) has a built-in fax/voice modem. How do I get it to work? I've tried fiddling with the network preferences and enabling the modem, but all to no avail.

Here's the error message. Does anyone have any idea? What I'd like to do is just print to a fax (as in Windows).

Cheers,

efax-0.9a: 53:53 Error: sync: modem not responding
efax-0.9a: 53:53 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 53:53 finished - unrecoverable error
efax-0.9a: 55:33 Error: can't open serial port /dev//dev/modem: No such file or directory

---

### Post by dwblas on 2006-11-29
> efax-0.9a: 55:33 Error: can't open serial port /dev//dev/modem: No such file or directoryIt looks like you don't have efax configured correctly. I would think that '/dev//dev/modem' should be '/dev/modem'.  Look in /dev first to make sure I am correct as modem might be in a subdirectory of /dev - I don't have a modem so I don't know.  Anyway, check the configuration file or see if efax has a (re)configure option and change it /dev/modem or whatever it actually is.

---

### Post by Dafydd on 2006-11-30
> **dwblas said:**
> It looks like you don't have efax configured correctly. I would think that '/dev//dev/modem' should be '/dev/modem'.  Look in /dev first to make sure I am correct as modem might be in a subdirectory of /dev - I don't have a modem so I don't know.  Anyway, check the configuration file or see if efax has a (re)configure option and change it /dev/modem or whatever it actually is.

thanks, i've tried readjusting things and think i've set /dev/modem rightly now, but there are still problmes.

if i type efax in a terminal i get:

efax: Thu Nov 30 16:38:52 2006 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 38:52 compiled Jun 21 2006 05:59:09
efax: 38:52 opened /dev/modem
efax: 38:53 using modem:1 in class 1
efax: 38:53 Error: unable to answer call
efax: 38:53 Warning: unexpected response "ERROR"
efax: 38:53 done, returning 3 (invalid modem response)



if i type gfax, i get the following error message:

ERROR: /undefinedfilename in (/home/dafydd/faxout/patents.ps</dev/null)
Operand stack:
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push
Dictionary stack:
   --dict:1122/1686(ro)(G)--   --dict:0/20(G)--   --dict:80/200(L)--
Current allocation mode is local
Last OS error: 2
ESP Ghostscript 815.02: Unrecoverable error, exit code 1



anyone have any ideas? i think this is one of the last problems i have with my sony vaio. i have given up on the motion eye webcam (just too difficult even though i see success reports).

dafydd

---

### Post by dwblas on 2006-11-30
Maybe try linmodems.org or the Sony forum, if they have one.  You can't be the only one whose's had problems.  Linux does struggle to keep up with all the of different modems out there.

---

### Post by srf21c on 2007-03-29
If you're in the USA you can also try sending a fax online for free using faxzero.com   

Just found out about it while researching Ubuntu compatible services that allow you to send faxes over the internet directly from your computer. 

Pretty cool, beats efax.com's minimum $17/mo.

---

