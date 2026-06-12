---
title: "cant get past partition during instal"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by SteveNorman on 2007-12-24
I have been running feisty, then gutsy well for awhile. I have a program I needed windows xp for, so I loaded it formating the hard drive thinking I would just reload Ubuntu later. I have a pentium dual processor, 80g hard drive w/1gig memory. I can run feisty from a live cd, but when I try to install it, it freezes up after the partition starts.
I have the partition slider set at about half, 38g I believe.

Am I missing something?

I am pretty new to partitioning, and very new to linux, so please state the obvious as I will miss it if you dont.
thanks

---

### Post by ~LoKe on 2007-12-24
Boot up the LiveCD and run gparted and modify the partition that way.  Then you can go ahead and install normally.

**EDIT**: Perhaps you should try running a Gutsy LiveCD first.

---

### Post by SteveNorman on 2007-12-24
sorry really new here,, how do I run gparted?, then how do I install after, just skip the partition portion?

---

### Post by ~LoKe on 2007-12-24
Just open up the terminal and type:
```
gksu gparted
```
It *should* open up gparted, and allow you to format/resize the partition in question, then during the installer you should be able to specify the mount points without re-partitioning.

I haven't had to do this in a while so perhaps this doesn't work anymore, or the installer is different.

Sorry, just posting the only solution I'm aware of.

---

### Post by SteveNorman on 2007-12-24
thanks Ill give it a try in the morning

---

### Post by SteveNorman on 2007-12-27
Didnt work, I made a live cd of gutsy, tried the gparted partitioner and it also locked up.
Still cant load past the partition portion of the loading process

---

### Post by rich.bradshaw on 2007-12-27
Did youshutdown windows, or just hibernate it?

---

### Post by SteveNorman on 2007-12-27
I believe I shut it down, I put the live cd in, hit start>shut down computer>restart

---

### Post by SteveNorman on 2007-12-29
hello?

---

