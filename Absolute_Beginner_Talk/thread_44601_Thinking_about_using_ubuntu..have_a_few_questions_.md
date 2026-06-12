---
title: "Thinking about using ubuntu..have a few questions :)"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by roach of discord on 2005-06-26
Hi everyone.  I'm not exactly new to linux, it is my main OS.  I currently use SuSE..however, sadly enough it's slower than hell (lol).

I've been thinking about using ubuntu (or kubuntu). 
 
In the past I've mainly used rpm and source based distros..so I'm not very familiar with debian. From what I've heard debian is very stable...but because of this...getting the *newest* software isn't easy? With ubuntu..can you use *bleeding edge* so to speak? For certain programs...especially amarok, gaim, mplayer etc...I prefer to use the newest, because in my opinion it only gets better. I don't especially want to be installing old software. 
 
 So basically, can you install the latest and greatest on ubuntu? :p.
 
 Also, what kind of package management programs does it use? Is it all command line, or are there GUI tools? I can use both...but however, sometimes prefer GUI when I'm lazy ;). I know it since it's debian based, it uses .deb files...but is installing software easy? Dependency issues? 
 
 I use to have dependency hell all of the time..but I've found that most newer distros have nice package management tools to get dependencies for you automatically.
 
 Also, how is multimedia support? This is a big issue for me, since I spend allot of my time listening to music (on amarok) and watching videos from time to time.
 
 Thanks!
 
 -RoaCh

---

### Post by ltmon on 2005-06-26
Hi there, I'm another SuSE convert now using Kubuntu.

Pros:
- (K)Ubuntu is _much_ faster that SuSE.  Much much faster.  I don't know what SuSE does differently, but I didn't realise how slow it was until I tried Kubuntu.

- I find it easier getting the latest packages in Ubuntu than I did in SuSE.  There's nothing about Debian packages themselves that make them more or less up-to-date... they are just a packaging schema.  The repositories that store packages are what matters.  The "old" reputation probably comes from Debian itself, whose stable distribution is always rather out of date (but rock solid).  Ubuntu releases a new version every 6 months, and most packages are the latest working versions.  Also there are many community contributed packages in the "backports" repositories that keep you bleeding edge if you wish.

- There are gui tools for package management.  Synaptic is best.

- Much better way of handling hot-pluggable (e.g. USB) devices than SuSE.

Cons:
- No YaST or equivalent for the most part.  Makes it harder to set up some more advanced things (such as Samba).

- Multimedia, Java, Flash not as good out of the box.  Very easy to add these though... just follow [http://ubuntuguide.org](http://ubuntuguide.org)

Hope this helps.

L.

---

### Post by roach of discord on 2005-06-26
Thanks.

I'm download kupuntu as I type this.  Looking forward to trying it out :)

---

### Post by poofyhairguy on 2005-06-27
> **roach of discord]
In the past I've mainly used rpm and source based distros..so I'm not very familiar with debian. From what I've heard debian is very stable...but because of this...getting the *newest* software isn't easy? With ubuntu..can you use *bleeding edge* so to speak? For certain programs...especially amarok, gaim, mplayer etc...I prefer to use the newest, because in my opinion it only gets better. I don't especially want to be installing old software. [/QUOTE]

Officially the software in Ubuntu doesn't change after a release. Luckily we have a person who backports everything we need. Look here:

[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

The latest and greatest...as stable as it can get for bleeding edge.

 [QUOTE]Also, what kind of package management programs does it use? Is it all command line, or are there GUI tools? I can use both...but however, sometimes prefer GUI when I'm lazy  said:**
> 
 
We have apt-get. It has a GUI wrapper called synaptic. It has access (once you do a few things) to over 15000+ software packages on the internet. It handles dependancies as well as you can. Package's are the strong part of Ubuntu.

Lack of a YAST for other configuration is the weak part.

[QUOTE]
 Also, how is multimedia support? This is a big issue for me, since I spend allot of my time listening to music (on amarok) and watching videos from time to time.


[http://ubuntuguide.org/](http://ubuntuguide.org/)

If you follow that guide....its the best multimedia compatibility Linux can offer.

---

