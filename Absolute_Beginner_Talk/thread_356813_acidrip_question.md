---
title: "acidrip question"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by thebes on 2007-02-08
well, first of all, many thanks for the forums. quite helpful

i am new to all this but figured out a few things, esspecially those connected to "add/remove" very good feature 

i am trying to convert a video using AcidRip and after choosing the bitrate, scale, codec and such i press "start". however i get "mencoder interrupted by user" even though i, the user, didnt interrupt anything 

any help is greatly appreciated

---

### Post by buuntuu! on 2007-02-09
i installed acidrip yesterday and stumbling upon your thread checked if the same problem would occur, but no... 
just a tought: have you got mplayer installed? i already had it installed so i have no idea if an acidrip-install gets you mplayer as well... check synaptic, maybe the solution to qour problem is just one click away:)

---

### Post by thebes on 2007-02-09
mplayer is installed

care to elaborate on how do i access synaptic and how does it relate in this case?

---

### Post by buuntuu! on 2007-02-09
sorry!
well, when installing mplayer gets you mencoder as well usually, which is the encoder acidrip uses... with synaptic you can check, if you have got it and install it, if not!
open your terminal```
sudo synaptic
```
to open synaptic with superuser-rights
search for mencoder

but if mplayer/mencoder is installed, i'm afraid i'm too much of a noob to help...
but a more experienced user will help you, i'm sure! the *buntu-folks are really helpful:)

---

### Post by jd65pl on 2007-02-09
To open graphical interfaces you should really use

```
gksudo *program*
```

---

### Post by Patrick K on 2007-02-09
My bad, I thought this was a thread about an acid trip. I thought that might be interesting.

---

### Post by buuntuu! on 2007-02-09
> **jd65pl said:**
> To open graphical interfaces you should really use

```
gksudo *program*
```

see what i mean with "helpful *buntu-folks"? even posting answers you find someone who will teach you something! thanks jd65pl:)
but any idea on what went wrong for thebes??

---

### Post by thebes on 2007-02-09
i find the file i wanna convert, i put the bitrate and size of the screen. it seems like the encoder used is mencoder. 

but once i start converting it just says "mencoder interrupted by user"

---

### Post by thebes on 2007-02-10
can anybody reccomend a different program that does similiar things?

---

### Post by buuntuu! on 2007-02-10
hm, i once found dvdrip in the repositories, just```
gksudo synaptic
``` as explained above, but i was not too happy with its interface so i didn't even take the time to find out how it works... 

but if you have got the time and want to find out *how* encoding works, try [http://www.ubuntuforums.org/showthread.php?t=273635&highlight=matroska]("http://www.ubuntuforums.org/showthread.php?t=273635&highlight=matroska"),  
its a command line solution, but don't be afraid, Heinz explains step by step and it's really interesting!

have fun, hope it helps.
b

---

### Post by thebes on 2007-02-10
that looks painful

---

### Post by buuntuu! on 2007-02-11
well, as i said, just if you have got the time and the drive;)
but it gets fun once you're into it (mind my signature...)
anyhow, i may have led you onto a wrong track, the problem is the stange behaviour of mencoder, so why don't you try a post in the multimediaforum[http://www.ubuntuforums.org/forumdisplay.php?f=138]("http://www.ubuntuforums.org/forumdisplay.php?f=138")
chances are, that somebody will have an answer for you there!

---

### Post by thebes on 2007-02-11
the culprit seems to be the codec, it works fine with lavc but not with xvid

---

### Post by sefs on 2008-03-12
I am having the same problem.  Acid rip was working for me before though.  dont know whats gone wrong now.

---

### Post by sefs on 2008-03-12
Ok i was able to solve my problem by switching the audio selection in acidrip to mp3lame...although i am 100 percent positive i was able to use lavc before.

---

