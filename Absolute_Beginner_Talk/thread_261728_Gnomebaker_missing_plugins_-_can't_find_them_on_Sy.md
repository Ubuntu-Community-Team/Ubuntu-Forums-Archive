---
title: "Gnomebaker missing plugins - can't find them on Synaptic"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-20
I'm tyring to burn mp3's but I keep getting prompted saying that gnomebaker "The plugin to handle a file of type audio/mpeg is not installed"

Any ideas?  thank you.


[IMG]http://i53.photobucket.com/albums/g56/learntobndg/Screenshot.png[/IMG]

---

### Post by croak77 on 2006-09-20
Gnomebaker uses gstreamer-0.8 , so you should install,
```

gstreamer0.8-lame
gstreamer0.8-mad
```

gstreamer0.8-lame is in multiverse and gstreamer0.8-mad universe.

---

### Post by 3rr0r on 2006-09-20
sweet sucess!  What I was extra proud of was I was able to guess the "sudo apt-get install" command !!  Now to see if it will burn correctly, thank you very much.

---

### Post by umphlette on 2006-09-21
Im not exactly a newbie here with linux but I'm baffled with this issue.  I have been getting the same error, whereas recently (last 2 or 3 weeks) I have not had this issue.  I have tried to re-install the relavant packages but that hasn't seemed to fix my problem.  I seem to recall an update not long ago to a codec or audio library...I wonder if that broke the system somehow?   I get the same error under K3B too.  Quite an annoyance this has been.  I'm going to be really really upset if I have to break down and tap my wifes WinXP to burn an audio cd...  On a side note I was having the Flash-Plugin Non-Free problem untill I completely removed the package.  Could that affect the audio library/codecs?

---

