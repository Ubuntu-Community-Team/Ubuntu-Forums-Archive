---
title: "[SOLVED] Why won't wireless work?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-03-09
I've been going NUTZ tryng to get something to work here... ndiswrapper, bcm43xx, and fwcutter don't work. 
Restricted drivers manager tells me I don't need a restricted driver. 

I've muddled my way through wireless issues before, (I even added the ones that worked for me into my signature line...) but this one is beyond me...

---

### Post by arochester on 2008-03-09
I have used this howto several times with success down to and including Problem 1: [http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+wireless+feisty](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+wireless+feisty)

---

### Post by mikeyphi on 2008-03-09
Can't believe you've got a problem after being here for the past 2 years!!

What's the card and/or what have you changed recently?

---

### Post by Papa-san on 2008-03-09
> **mikeyphi said:**
> Can't believe you've got a problem after being here for the past 2 years!!

What's the card and/or what have you changed recently?

LOL!

Yeah... on my old latitude, I can do the wireless in my sleep... I just bought Dell 1525's for my wife and daughters...
 These have the 1395 wlan mini card, also known by 'bcm4310 (rev 01)' My old one is the 4306

I've just finished re-installing Gutsy, and it's almost done doing the 195 updates over ethernet.

---

### Post by mikeyphi on 2008-03-09
Pity you couldn't get the Dell's pre-installed with Ubuntu!! 

I see from Hardware support that the 4310 (rev01) is a bit tricky to setup - good luck!!

---

### Post by Papa-san on 2008-03-09
Yeah... My wife wanted to be sure they were all set up with windows because of how difficult Ubuntu is to set up... From the looks of it, yet again, she is right... (Yeah, I get a slice of humble pie every time I mention it...)

---

### Post by Papa-san on 2008-03-09
Nope... No good
Meaning this: 

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) failed at sudo rmmod bcm43xx:
```
tiffany@tiffany-laptop:~$ sudo rmmod bcm43xx
[sudo] password for tiffany:
ERROR: Module bcm43xx does not exist in /proc/modules
tiffany@tiffany-laptop:~$ 

```
Also had a suggestion:

1. sudo apt-get update
2. sudo apt-get install bcm43xx-fwcutter
3. sudo modprobe bcm43xx
4. restart
that didn't work... Did that before I did the one above... Any significance to the fact that it didn't find the bcm43xx module?

---

### Post by Papa-san on 2008-03-09
Nothing I try works...
Mods, Please delete this thread, and I'll delete the Ubuntu partitions from this machine.

There's the 'Solution' :-D
Saves me from having to waste my time on two additional systems as well. Those can stay clean.

---

