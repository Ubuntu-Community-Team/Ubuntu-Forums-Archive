---
title: "Frame rate slows down suddenly"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-11-23
My frame rate has suddenly slowed down. Running glxgears, the gears start nice and fast for about 3 seconds, then suddenly slowed down to jumpy motion. 
Now it buggers up games as well. My kids love Supertux, but it now only plays right if I unselect GLcore option. 
I reconfigured xserver as well, no change, same for changing my xorg.conf file. Nothing has changed there in any case to my previous back-ups. 
I've read and searched the forums and went through a lot of hard won set-ups, but nothing helps. 

Personally I feel I should never have upgraded to Breezy, too many things are now broken with no fix, just generic advice. Hope the generic advice will stay absent on this thread....

---

### Post by apjone on 2005-11-23
[QUOTE=GrootBrak]My frame rate has suddenly slowed down. Running glxgears, the gears start nice and fast for about 3 seconds, then suddenly slowed down to jumpy motion. 
Now it buggers up games as well. My kids love Supertux, but it now only plays right if I unselect GLcore option. 
I reconfigured xserver as well, no change, same for changing my xorg.conf file. Nothing has changed there in any case to my previous back-ups. 
I've read and searched the forums and went through a lot of hard won set-ups, but nothing helps. 

Personally I feel I should never have upgraded to Breezy, too many things are now broken with no fix, just generic advice. Hope the generic advice will stay absent on this thread....[/QUOTE]

you need a 3d accelartor enabled graphics card as try and d/l GL support packages

---

### Post by GrootBrak on 2005-11-23
HOG!!! Why was is working previously?
I found the real reason, but not a solution. Problem is XORG sucking my CPU dry. Now I know why screensavers and simple games cooked my CPU into overheating.
Read this thread below
[http://www.ubuntuforums.org/showthread.php?t=18197&page=16&highlight=glxgears+frame+rate](http://www.ubuntuforums.org/showthread.php?t=18197&page=16&highlight=glxgears+frame+rate)

Anyone have similair issues with xorg draining the cpu?

---

