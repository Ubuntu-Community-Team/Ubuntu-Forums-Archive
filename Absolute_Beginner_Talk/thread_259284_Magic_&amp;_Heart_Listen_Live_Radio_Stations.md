---
title: "Magic &amp; Heart Listen Live Radio Stations"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by HushTheVoices on 2006-09-17
I've installed Ubuntu 6.06 for a PC I built myself for my mother-in-law and in general it's working fine, but she would like to 'listen live' to Magic FM: [www.magic.co.uk](www.magic.co.uk) and Heart 106.2: [www.heart1062.co.uk](www.heart1062.co.uk) - via her PC.

From what I've gathered so far, they are geared up for playing via Windows Media Player (bah!).  I've installed the w32codecs package, XMMSPlayer and gstreamer so I can play the various radio stations these programs provide, but it still refuses to play the stations she really wants.  With Magic it seems to want the Windows Media Player plug-in for Firefox and with Heart it tries to launch in to Movie Player.

I've looked at the restricted forums page and done a general search on these forums and on google, but none of the info seems to cover exactly what I need.  I'd be greatful for any assistence.

Many thanks

As a side note can anyone recommend a free program where it allows me to share/control her PC desktop from my Windows XP Home PC (eg like Remote Assistance or WebEX)

---

### Post by xpod on 2006-09-17
> I've installed Ubuntu 6.06 for a PC I built myself for my mother-in-law 

OH DEAR.............NOT you toooo:biggrin: 

Never quite got as far as "buiding" the MIL`s but i have left half her 111g HD Unallocated after i re-installed her XP.:confused: #-o ](*,) 

I dread the phone going now so i do....
Unfortunately i did`nt have the luxuary of XP cd`s so i had what could only be described as a "nightmare"...twice!!

Beware of MIL`s and their PC`s...clicky clicky clicky,,,LOL

EDIT:> from my Windows XP Home..WHAT?...NO UBU?????

---

### Post by ron999 on 2006-09-17
Hi hushthevoices

I've just tried those two radio stations.
magic works ok. I don't know which player it's using though. It just opens up a player on the webpage and runs. I think that you may be missing a codec.
As for heart, it opens up totem and then says it can't run it. I don't know what the solution to this is, it's an mmms stream.

---

### Post by xyz on 2006-09-17
Try this:
[http://www.ubuntuforums.org/showthread.php?t=250416&highlight=internet+radio](http://www.ubuntuforums.org/showthread.php?t=250416&highlight=internet+radio)

---

### Post by ron999 on 2006-09-17
Hi hushthevoices
I've managed to get heart running.
Open the terminal and paste this in:-
mplayer mms://live2.interoutemediaservices.com/heart1062

edit, a better link instead

---

### Post by senn on 2006-09-17
hi ron999, i went to the heart site and tried to play the site in totem. when i clicked on listen i was asked to run the app that you outlined on your last reply. when i put the line into terminal this is what i got.senn@senn-desktop:~$ mplayer mms://cpg-wm.interoutemediaservices.com/chrysalis/protected/heart1062.wma?tk=CIsa3mKoyAg=BtjSJulxvkhvCtQeoOBlH GCmR5A=*2
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing mms://cpg-wm.interoutemediaservices.com/chrysalis/protected/heart1062.wma?tk=CIsa3mKoyAg=BtjSJulxvkhvCtQeoOBlH.
STREAM_ASF, URL: mms://cpg-wm.interoutemediaservices.com/chrysalis/protected/heart1062.wma?tk=CIsa3mKoyAg=BtjSJulxvkhvCtQeoOBlH
Resolving cpg-wm.interoutemediaservices.com for AF_INET6...
Couldn't resolve name for AF_INET6: cpg-wm.interoutemediaservices.com
Resolving cpg-wm.interoutemediaservices.com for AF_INET...
Connecting to server cpg-wm.interoutemediaservices.com[212.23.58.132]: 1755...
Connect error: Connection refused
Resolving cpg-wm.interoutemediaservices.com for AF_INET6...
Couldn't resolve name for AF_INET6: cpg-wm.interoutemediaservices.com
Resolving cpg-wm.interoutemediaservices.com for AF_INET...
Connecting to server cpg-wm.interoutemediaservices.com[212.23.58.132]: 80...
read: Connection reset by peer
Failed, exiting
STREAM_HTTP(2), URL: mms://cpg-wm.interoutemediaservices.com/chrysalis/protected/heart1062.wma?tk=CIsa3mKoyAg=BtjSJulxvkhvCtQeoOBlH
Resolving cpg-wm.interoutemediaservices.com for AF_INET6...
Couldn't resolve name for AF_INET6: cpg-wm.interoutemediaservices.com
Resolving cpg-wm.interoutemediaservices.com for AF_INET...
Connecting to server cpg-wm.interoutemediaservices.com[212.23.58.132]: 80...
Read failed.
File not found: 'cpg-wm.interoutemediaservices.com/chrysalis/protected/heart1062.wma?tk=CIsa3mKoyAg=BtjSJulxvkhvCtQeoOBlH'
Failed to open mms://cpg-wm.interoutemediaservices.com/chrysalis/protected/heart1062.wma?tk=CIsa3mKoyAg=BtjSJulxvkhvCtQeoOBlH

Playing GCmR5A=*2.
File not found: 'GCmR5A=*2'
Failed to open GCmR5A=*2


Exiting... (End of file)
senn@senn-desktop:~$

can you show me what i'm missing as now i'd realy like to get this running just so i can har har](*,)

---

### Post by ron999 on 2006-09-17
Hi senn
I've edited the link to paste, it's a different one now.
This one:-
mplayer mms://live2.interoutemediaservices.com/heart1062

---

### Post by senn on 2006-09-17
hi ron999, your the man that last link works a treat, but, i can only play heart when the terminal is open, is this a common problem or , as i suspect , my mplayer is missing something. also like hushthevoices magic wont play either.:confused:

---

### Post by ron999 on 2006-09-17
Hi senn
I don't know what to do about heart radio, maybe someone else will come up with a more slick solution than using the terminal.
As for magic radio, perhaps you are missing a codec. I installed all the codecs at once using Automatix.

---

### Post by senn on 2006-09-17
hi ron999, you were right on the money with the codecs from automatix, i thought i had downloaded all i needed already](*,) as you have probable guessed im new to all this copy/paste, terminal stuff#-o  but with folk like you to help out i think i will graduly get the hang of it. cheers and keep posting. senn.=D>

---

### Post by ron999 on 2006-09-17
Sorted:D

---

### Post by HushTheVoices on 2006-09-17
OK Ron999, I'll try both of those solutions (automatix and the terminal command line) many thanks for your help :) =D>

Anyone got any idea's on the remote support thingy - would it be easier if I installed Ubuntu too?

---

