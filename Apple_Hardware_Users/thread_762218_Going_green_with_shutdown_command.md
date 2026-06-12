---
title: "Going green with shutdown command"
date: 2008-04-21
forum: Apple Hardware Users
---

### Post by stream303 on 2008-04-21
My G5 iMac lacks any sort of hibernate or standby, but I still wanted to save energy.  I'm usually pretty good about shutting down manually, but sometimes forget about it when the screensaver is black and I can't hear the machine running.

I was checking out Dirk's nice blog and it hit me - why not keep it simple?

[http://linuxtidbits.wordpress.com/](http://linuxtidbits.wordpress.com/)

In the past I just memorized the shutdown command but never really bothered to read the man page.

Simple solution: just use the shutdown command with a delayed response.

Shutdown 4 hours from now:
```
sudo shutdown -h +240
```

Shutdown at 11:30 pm:
```
sudo shutdown -h 23:30
```

I just run this in a terminal and then minimize it.  For convenience, I just rename the terminal to "shutdown" and when I call it up, I can see how close I am to shutdown, or just cancel it completely with a CTRL-C.

Until they release full specs on the G5, this is the best I can do so far.

** **UPDATE*****  For an even better way to shutdown based on user-inactivity, see:
[http://ubuntuforums.org/showthread.php?t=530973](http://ubuntuforums.org/showthread.php?t=530973)

---

### Post by stream303 on 2008-04-22
oops.  Tried to shutdown via the gui with a shutdown already running in a terminal, and it logs you out and brings you back to the gdm login.

Guess you have to kill the delayed-shutdown in the terminal first. :)

---

### Post by flitcher11 on 2008-07-03
Hi,
'Keep the city green' is the consumer's guide to the green revolution. Make going green a part of your daily life. That will ensure longer life for all and healthier one as well.
====================================================
flitcher

[http://www.goinggreenbuzz.com ]("http://www.goinggreenbuzz.com")

---

