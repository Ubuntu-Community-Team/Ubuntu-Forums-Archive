---
title: "vnc4server vs. x11vnc ?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-28
What's the difference between **vnc4server** and **x11vnc**?
I've seen tutorials for both, and I am confused, which is better? 
Does one outperform the other or are they generally just the same thing w/ 2 different ways of going about things?

---

### Post by bodhi.zazen on 2008-02-28
They are roughly equal in performance.

x11vnc = share a session ie share the same screen local and remote ; users share a screen and can see what each other is doing.

vnc4server = separate , non-shared sessions. ie local = 1 session, remote = second session. users do not share a session and are independent of each other.

---

### Post by BassKozz on 2008-02-29
> **bodhi.zazen said:**
> vnc4server = separate , non-shared sessions. ie local = 1 session, remote = second session. users do not share a session and are independent of each other.

Maybe I am getting these confused then, because I don't have x11vnc installed, but I do have vnc4server installed and when I VNC into my machine it is the same "shared" session as if I was behind the terminal. :confused:

---

### Post by bodhi.zazen on 2008-02-29
Not sure from your description. If you are using the default VNC server it is vino

If you are not sure, you could search in synaptic.

See if this kink help you at all :

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

Also the FreeNX VNC server is faster

[uwiki]FreeNX[/uwiki]

HTH

---

### Post by BassKozz on 2008-02-29
> **bodhi.zazen said:**
> Not sure from your description. If you are using the default VNC server it is vino
Ahh, yes that is it, when I run 'top' while vnc'ing, I noticed a process called vino...
So I guess I am not using vnc4server after all :razz:
> **bodhi.zazen said:**
> Also the FreeNX VNC server is faster
FreeNX is faster?
How much faster are we talking?

---

### Post by bodhi.zazen on 2008-02-29
Not sure of the benchmarks, but it should be noticeably faster.

[http://en.wikipedia.org/wiki/FreeNX](http://en.wikipedia.org/wiki/FreeNX)

---

### Post by szandor on 2008-03-02
nx is not for the fainthearted. well, considering if you've never used it before. it took me a couple of hours to really read through everything on top of getting the server/client working, and there's still random cool things i still haven't touched upon. i would suggest sticking with vncserver or the like and use vncviewer to connect to the server. if you want to connect to the native display, i.e. :0, use x11vnc. or even vino-server if you use gnome. the differences between nx (i use nomachine's as i only need to connect to 2 boxes at the same time at the most) and any other virtual server was not noticeable either locally on the network or across the internet. although, messing with server.cfg and node.cfg helped speed things up between the client and server. also, (obvioulsy, i prefer nomachine) all the issues i ran into were answerable through [www.nomachine.com's](www.nomachine.com's) support pages. if you can't resolve something there, i would suggest sticking with vncserever or x/ssh forwarding. if you decide to use freenx or nomachine's nxserver, i would suggest keeping your changes to /usr/NX/home/nx/.ssh/sshd_config and leave /etc/ssh/sshd_config alone. also, if you make a change in server.cfg, make sure you make the same change in node.cfg if applicable. oh and your private keys are important.

---

### Post by reidkaufmann on 2008-03-05
NX isn't even for the intrepid some times.  They claim to have an opensource server, but I was not able to get it working with their NX client (which is closed source).  I haven't tried again recently, but unless they've cleaned up their act you'd better have a lot of time to kill if you want freenx to work.

I did get things working with the non-free NX server, but it stopped working after the evaluation period ended.

---

### Post by szandor on 2008-03-16
> **reidkaufmann said:**
> I did get things working with the non-free NX server, but it stopped working after the evaluation period ended.

there are, i believe, 2 license files that need to be replaced. you should be able to remove then re-install the nx package to replace the license files. your keys should stay the same but i would backup whatever config files you're using.

---

