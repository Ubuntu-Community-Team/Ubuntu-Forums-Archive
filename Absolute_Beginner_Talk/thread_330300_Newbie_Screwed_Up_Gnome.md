---
title: "Newbie Screwed Up Gnome"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Real Newbie on 2007-01-02
I have been looking at LINUX for several weeks. Ran a couple of live CD's and decided to install UBUNTU. Everything seemed to go fine except I couldn't seem to get my screen resolution right. I found a post that talked about using Xconfig??? Seemed like a knowlegable person. I tweaked the file until I got the resolution almost to where I wanted...then I screwed something up! Ahhhhhh....I rebooted, but Gnome won't start. I am at the command line and ain't got a clue what I am doing.

If anybody has any way to get me back, besides reloading, please help. Naturally I did not back up a config file, that would have been too smart.

Please make the suggestions as basic and step by step as possible.

Thx for any help.

---

### Post by Jorge32 on 2007-01-02
what changes did you made on xconf? 
When you rebooted you could hear the drums of the log-in of Ubuntu?

---

### Post by MkfIbK7a on 2007-01-02
start the comand line and do
```
sudo dpkg-reconfigure xserver-xorg
```
answer the questions correctly

---

### Post by r4ik on 2007-01-02
Any error messages ?

---

### Post by r4ik on 2007-01-02
> **wert613 said:**
> start the comand line and do
```
sudo dpkg-reconfigure xserver-xorg
```
answer the questions correctly

Yep.

---

### Post by Real Newbie on 2007-01-02
I tried that and recieved 
dpkg: conflicting actions --control and --remove

Ideas?

---

### Post by Real Newbie on 2007-01-02
Also no drums.

---

### Post by MkfIbK7a on 2007-01-02
if you have nothing important i recomend reinstalling ubuntu

---

### Post by r4ik on 2007-01-02
sudo dpkg-reconfigure xserver-xorg

Sure you typed it as is ?

---

### Post by gunksta on 2007-01-02
You could also try posting your xorg.conf file on this thread and tell us what kind of hardware you have.

The problem might be really easy for someone here to spot.

--andy

---

### Post by r4ik on 2007-01-03
This is why i ask seems to give the error (sometimes)

 sudo dpkg-reconfigure xserver-xorg
I thought there was spaces inbetween the reconfigure and the xserver-xorg

From another post.

---

### Post by malcolmb on 2007-01-03
I did the same thing to my first Ubuntu install, and what I did was just a re-install.

I know that's not the answer you want if you saved some important stuff on there, but if you haven't then go ahead then start anew.

Backup your important stuff, but don't stop experimenting and breaking things.  Just try not to do the same mistake too many times.

---

### Post by kdub432 on 2007-01-03
Try this.... it might just work
from grub, select recovery mode
enter your root password for maintanence
then type

cp /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf

if i'm not mistaken, that will restore your original xorg.conf file....
no guarantees though

---

### Post by Real Newbie on 2007-01-03
All,
Thanks for the help. I had not really done anything important so I reloaded and all is well. My purpose installing UNBUNTU is to learn more about LINUX and to see if I can junk my Win machine. Just tired of all of the lock ups and reboots. To that point I pulled an old Intel Nightshade server out of the attic, loaded up UNBUNTU and am playing with it for awhile. I am writing this msg on it in UNBUNTU.

Now, before I start fooling with this again. Can anybody point me to some good info on back up and restore?

One more thing, I am truly impressed by the response to my problem. This is an amazing forum! Thanks for all  of the help.

---

### Post by xfceslacker on 2007-01-03
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by k1001001 on 2007-01-03
ignore.

---

