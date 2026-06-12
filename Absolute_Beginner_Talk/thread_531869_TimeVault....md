---
title: "TimeVault..."
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-08-22
Hello,

I was wondering if, even in its early stage, TimeVault is something worth installing and if it is, can it be used despite me lacking an external hard-drive? Also, is it very hard to set-up and get running?

Thanks for any responses in advance!

---

### Post by isaacj87 on 2007-08-22
Bumping it up.

---

### Post by oilchangeguy on 2007-08-22
this may help:
[http://ubuntuforums.org/showthread.php?t=474973](http://ubuntuforums.org/showthread.php?t=474973)

---

### Post by isaacj87 on 2007-08-22
I appreciate the response...but I still need a little more info

Can I use TimeVault even though I don't have an external harddrive?

---

### Post by Jimmyfj on 2007-08-22
I used TimeVault when i ran Ubuntu 7.04 32 bit and I have never had any issues with the program. I even tested it on my 6.10 Edgy server install, still no issues. But the software are in development, remember that.

---

### Post by isaacj87 on 2007-08-24
Did you use an external harddrive?

---

### Post by isaacj87 on 2007-08-25
Can I get some more responses??

---

### Post by Jimmyfj on 2007-08-25
> **isaacj87 said:**
> Can I get some more responses??

In TimeVault you can set the primary folder you want to save your snapshots/Images to. Just enter the settings by right-clicking on the Vault icon and select the default save folder. This can easily be an external drive. But an external hard drive is no "must have" to run TimeVault - You deside the folder yourself. You even get to decide on the time between the snapshots in minutes or hours.

---

### Post by isaacj87 on 2007-08-25
Thanks for the response!

I might have to try this thing out...

---

### Post by Staz69uk on 2007-11-08
I just tried TimeVault and it is a bit of a disaster to be honest.

It almost worked for a while; at least it gave me a list of "metadata" entries.  It never actually seemed to back up any of my data though.  A test restore failed miserably (can't remember the error message).

I thought I'd try raising a bug report, but now it doesn't seem to work at all - the tooltip on the notifier says "Disconnected" and I can't get it to do anything. 

The Nautilus integration is broken, but the release note mentions this so I guess that isn't surprising.  

I tried a "timevault restart" and it locked my session up.  Had to Ctrl-Alt-F5 and kill -9 the timevault processes.

I'm going back to evaluating "[FlyBack]("http://code.google.com/p/flyback/")".  

I might try TimeVault again in a few months and see if it has improved.  The 0.7.5-1 package was labeled a "Beta candidate" but it obviously isn't ready for that yet.

---

