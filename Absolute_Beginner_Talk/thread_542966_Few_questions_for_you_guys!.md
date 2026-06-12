---
title: "Few questions for you guys!"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Chuck_Schuldiner on 2007-09-04
Whats up guys!

First of all Im a first time Ubuntu user and I like it.  I come from a Windows background and I decided to give it a try . But to be honest with you guys for about a week I have been reading almost all the posts here for troubleshooting Networking and I got it working fine thanks to you guys, Now the Beryl installation is giving me problems. I go to the Synaptics and I cant find it and I cant install it,  neither that Compiz program that everyone talks about. 

How do I get something else other than the basic graphics and basic effects that come with ubuntu?  My only problem is that I felt kind of shy of posting because I basically dont understand most of the computer language that most of you experienced users use.

Can anyone help? please.  My graphics card is installed and in use but when I try to enable background Effects I get an error "the composite extension is not available"  

I feel bad telling you guys this but Im clueless to be honest I even bought a Linux guide to learn how to use it and still struggling with it.

Can anyone help me with some clues please!!!!!

---

### Post by sbassett on 2007-09-04
If you feel brave check out [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104) , which gives links to all guides for Beryl, Compiz and Compiz Fusion. Never feel bad about asking a question, it's the best way to learn.

---

### Post by Niklas Schröder on 2007-09-04
your computer may not support opengl which is ESSENCIAL to compiz/beryl.  try to run...

```

glxgears

```

(just in case you don't know how to run, hit "ALT>>F2" and enter the command in the box)

if it runs smoothly, then you probably have compositing (aka: opengl) enabled and running, if it's choppy you either don't have it enabled or it's not on your machine.

---

### Post by Niklas Schröder on 2007-09-04
have you tried installing compiz fusion by following [THIS](http://ubuntuforums.org/showthread.php?p=2895086) tutorial?

---

