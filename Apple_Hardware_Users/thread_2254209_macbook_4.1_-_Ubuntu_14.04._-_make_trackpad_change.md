---
title: "macbook 4.1 - Ubuntu 14.04. - make trackpad changes permanent"
date: 2014-11-25
forum: Apple Hardware Users
---

### Post by david.losonci on 2014-11-25
I seem to have a problem with my trackpad on Ubuntu 14.04.

My macbook 4.1 recognizes the trackpad on startup, but I have to use great pressure to move the cursor around.

The command line 
```
xinput --setprop 12 "Synaptics Finger" 10 10 10
```

does solve the problem, but after rebooting the machine I have to type in the command into the terminal every time.

How can I make changes permanent or is there a better way to fix the trackpad?

Thanks for any answers

---

### Post by david.losonci on 2014-11-30
ok, I found a solution myself, in this forum :p

[http://ppcluddite.blogspot.co.at/2013/06/getting-usable-trackpad-on-aluminum.html?m=1](http://ppcluddite.blogspot.co.at/2013/06/getting-usable-trackpad-on-aluminum.html?m=1)

---

### Post by nils32 on 2014-12-01
How hard was it to install 14.04 on your macbook 4.1? Did you face any problems while installing?

I'm curious because I wanted to do just this (or even 14.10), but I found lots of posts online indicating that it's pretty hard / unsupported.
Thanks!

---

### Post by david.losonci on 2014-12-02
hey nils32,

Basically everything worked out of the box except the trackpad thing and the iSight camera ([https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)). However, I could fix both problems. Everything is running great now.

 I am single booting FYI.

Dave

---

