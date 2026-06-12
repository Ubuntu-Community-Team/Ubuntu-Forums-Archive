---
title: "[SOLVED] BIG problem with logging in to Ubuntu on Mac Mini!"
date: 2008-12-09
forum: Apple Hardware Users
---

### Post by foolio1990 on 2008-12-09
I've got an intel based Mac Mini with Ubuntu installed on it, (as well as Windows XP and OS X) I have been able to log in and use the ubuntu, All I have done is update it. But now, when I turn on the Mac Mini, select to boot Ubuntu (from rEFIt), it boots up to the log in screen, I put in my log in and password (correctly, might I add) and when I hit enter, the screen goes brown like it's loading up, but then it goes black, my 21" Apple Monitor blinks 3 times consecutively. Does anybody have any idea what my problem could be? Thanks in advance.

---

### Post by Tommy on 2008-12-09
> **foolio1990 said:**
> I've got an intel based Mac Mini with Ubuntu installed on it, (as well as Windows XP and OS X) I have been able to log in and use the ubuntu, All I have done is update it. But now, when I turn on the Mac Mini, select to boot Ubuntu (from rEFIt), it boots up to the log in screen, I put in my log in and password (correctly, might I add) and when I hit enter, the screen goes brown like it's loading up, but then it goes black, my 21" Apple Monitor blinks 3 times consecutively. Does anybody have any idea what my problem could be? Thanks in advance.

It sounds to me like X (xserver) is getting confused... if you just upgraded from Ubuntu 8.04 Hardy to Ubuntu 8.10 Intrepid, this is actually very likely, as the newer version of X still has some kinks.

The first thing to do is see if you can bring up a console -- after you get to the brown or black screen, press ctrl-alt-F2 (the alt key on a Mac is also labeled "option"). You should then be able to log in. After supplying your username and password, you should be able to work on it.

I was going to recommend just configuring the xserver using this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```but I see a thread here [https://answers.launchpad.net/ubuntu/+source/xorg/+question/49764](https://answers.launchpad.net/ubuntu/+source/xorg/+question/49764)  that offers some more good advice, and I think you might possibly also need [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

