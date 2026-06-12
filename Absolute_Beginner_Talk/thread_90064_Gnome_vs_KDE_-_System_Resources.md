---
title: "Gnome vs KDE - System Resources"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by derbaschti on 2005-11-14
Hi, 

I have installed both Gnome and KDE on my HP nx9005 laptop. Although I really like the way KDE looks, it seems to me, that it uses much more of my computer's resources. (When I do absolutely nothing, about 400 MB of RAM are in use, wheras under Gnome it's just about 100 MB) 

Is this normal or just a problem of my configuration? 

Thanks for your help,

Sebastian

---

### Post by Pablo_Escobar on 2005-11-14
There can be some configuration switches that can save You some RAM in KDE (Gnome also). 
IMO Gnome uses less resources because of less eye-candy that KDE is so full of.
But maybe someone may prove I'm wrong :D

---

### Post by raublekick on 2005-11-14
On my box they eat up about the same (Gnome actually a little more).  Same with XFCE... maybe I'm getting a wrong reading?

---

### Post by loupy on 2005-11-14
I actually find KDE to be slighty less resource intensive.  Is it actually using 400MB or is that the memory used counting the buffered/cached space?

from terminal type in free -m and it will show you a list of actual memory used and buffered/cached memory.

On mine it shows:

                 total       used       free     shared    buffers     cached
Mem:          1011        718        293          0        140        351
-/+ buffers/cache:        225        785
Swap:            0          0          0


So although it shows I am using 718MB of ram 140MB is buffers and 351MB is cached so I am actually using 225MB.  (and I have quite a few apps running right now)

---

### Post by Darrin on 2005-11-14
Im Gnome and here are my stats.

                 total       used       free     shared    buffers     cached
Mem:          1012        792        220          0         67        464
-/+ buffers/cache:        260        752
Swap:         1851          0       1851

---

### Post by chazzjazz on 2005-11-14
Thats Huge....but I Guess You Have To Keep Up With The Joneses

---

### Post by clparker on 2005-11-14
Well, Understand now that for the last six months (maybe more), software has been actually starting to 'catch-up' with the hardware on the market. Remember w/ service pack 2, a newer antivirus, IE 6, and other apps, you need to have at LEAST 512 MB RAM w/ windows, and I know ubuntu needs at least 256 just to be bearable.

---

### Post by tseliot on 2005-11-14
[QUOTE=derbaschti]Hi, 

I have installed both Gnome and KDE on my HP nx9005 laptop. Although I really like the way KDE looks, it seems to me, that it uses much more of my computer's resources. (When I do absolutely nothing, about 400 MB of RAM are in use, wheras under Gnome it's just about 100 MB) 

Is this normal or just a problem of my configuration? 

Thanks for your help,

Sebastian[/QUOTE]

KDESysmonitor doesn't display the correct amount of RAM in my system:

It says the RAM in use is 1.4GB (I have 2GB RAM). However if I type:

```
top
```

I get the exact amount of RAM in use.

Aysiu mentioned this command in a previous post.

---

### Post by Topsiho on 2005-11-14
Linux has a tendency to use as much of the available memory as it can. Whether in Gnome, KDE or just text.

This is quite OK, what else do you have all this memory for? :)

It's nice to have a system which uses the resources that are available to it.

Of course KDE needs quite a lot of memory just to be happy, so does Gnome. I think both need at least 250 MiB, where a text-system neeeds far and far less than that. You cannot have a whale in a bath tub, in which you can put a guppy :)

Topsiho

---

