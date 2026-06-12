---
title: "Making dvd movie"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by jdm2 on 2006-11-07
I have some video file for example .avi files and I would like to make a playable dvd.  I know how to make a data dvd but I would like to make a dvd that I could put into a dvd player and be able to watch it.  I was wondering how I would go about this.  Thanks for the help in advance.

---

### Post by NT4usB on 2006-11-07
Might start [here]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+make+dvd+from+avi&btnG=Google+Search")

---

### Post by taurus on 2006-11-07
It's called DeVeDe...

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by shingalated on 2006-11-07
Yeah, DeeVeeDee works great, I tried it the first time the other day with a couple of .avi's and I was really impressed with the simplicity of the program and the speed.  It only took about 45 minutes to encode a full length movie!

---

### Post by taurus on 2006-11-07
> **shingalated said:**
> Yeah, DeeVeeDee works great, I tried it the first time the other day with a couple of .avi's and I was really impressed with the simplicity of the program and the speed.  It only took about 45 minutes to encode a full length movie!
And about 15-20 minutes to burn it to a DVD using k3b!!!  ;) 

In other words, it takes only a little more than an hour before you can watch it on your big tv...  8)

---

### Post by JayTee on 2006-11-07
> **taurus said:**
> It's called DeVeDe...

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

I tried DeVeDe but had all kinds of issues with the video audio sync both during preview and during playback on DVD players after burning. If you can get it to work with everything sync'd it's great and the interface is one of the best I've used. I've been using Tovid ([http://tovid.org](http://tovid.org) but stop short of burning in the GUI and use a bash script to run a mkisofs script that uses dvdauthor to make a DVD file structure and build it into an ISO file. Only way so far I've gotten solid quality DVD output that plays on a DVD player.

---

### Post by Russty of Oz on 2006-11-08
I can't work out how to install devede!  I have checked "How to install anything in Ubuntu" but there is no config or make file in devede.  

Can someone help?

---

### Post by findus on 2006-11-08
> **Russty of Oz said:**
> I can't work out how to install devede!  I have checked "How to install anything in Ubuntu" but there is no config or make file in devede.  

Can someone help?


You can get it throguh Synaptic - just search for devede . Worked for me!

---

### Post by findus on 2006-11-08
You will need to have the universe repository enabled.  You will also need to install vcdimager at the same time through synaptic.

---

### Post by Russty of Oz on 2006-11-08
Oh!  That was easy.

Thanks :D

---

### Post by taurus on 2006-11-08
> **JayTee said:**
> I tried DeVeDe but had all kinds of issues with the video audio sync both during preview and during playback on DVD players after burning. If you can get it to work with everything sync'd it's great and the interface is one of the best I've used. I've been using Tovid ([http://tovid.org](http://tovid.org) but stop short of burning in the GUI and use a bash script to run a mkisofs script that uses dvdauthor to make a DVD file structure and build it into an ISO file. Only way so far I've gotten solid quality DVD output that plays on a DVD player.
Yes, tovid is another option but it takes a long time to decode one avi, hours...  I've used both but always spend more time using devede because it's easy and fast.

And of course, you can do it from a command line too and there is a big HOWTO here so search for it.

---

### Post by Nawaz on 2007-11-06
I am totally new to the world of Linux, switching from M$ indows. I have a .mp4 file that I want to burn to DVD to share with my family overseas (PAL system). I do not know the command line programming in Linux. Any guidance to accomplish this task in GUI will be welcom. I am running Ubuntu 7.10 i386.

---

