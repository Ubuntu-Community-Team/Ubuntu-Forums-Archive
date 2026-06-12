---
title: "Took puter to repair shop now Ubuntu is not working"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by georgie_o on 2007-09-04
Computer was acting pretty strange this weekend- making an odd ticking noise and crashing and freezing at random points during Bios, Windows and Ubuntu so thought I'd get it checked out at the repair shop and get my new shiney Nvidia graphics card put in at the same time. 

They couldn't find any problems, but installed the card and drivers on Windows, all works fine on this partition. But I boot up Ubuntu (I only have WoW and Firefox on this side of the pc- I do everything else on Ubuntu) and I get:
Failed to start X server
kinit: no resume image, doing normal boot...
and Restart GDM when configured correctly.

So is this something that's to do with needing to get the correct Nvidia drivers installed on Linux partition or is this something some guy in a shop has messed up by doing something in Windows or other (?)

Most importantly is there a way to recover (have tried recovery mode, but nothing happened) or am I going to have to reinstall everything?? And is there a command to launch the GUI-desktop?

Any help is greatly appreciated. Thanks

---

### Post by yabbadabbadont on 2007-09-04
When you say that nothing happened when you tried recovery mode, what exactly do you mean?  It should have dropped you into a text mode command prompt.  Assuming that it did so, you can reset your Xorg configuration to the safe, installation default by running this:
```
sudo dpkg-reconfigure -p high xserver-xorg
```  Then just enter the "reboot" command at the prompt to restart.

---

### Post by timzak on 2007-09-04
I believe that is a pretty normal thing to happen when you change the graphics card in an Ubuntu system.  I have notes at home on how to recover from this, but I can't get to them for a few more hours at least.  By then I'm sure someone else will step up and provide the info.

Wait, I remember helping someone with this awhile back.  I just found the thread.  Here's the link, find my post on page 2 of the topic and that should give you all the info you need to get back up and running:

[http://ubuntuforums.org/showthread.php?t=466174](http://ubuntuforums.org/showthread.php?t=466174)

---

### Post by georgie_o on 2007-09-04
Thanks for the quick replies! Safe mode did exactly the same as normal mode (what I meant by 'did nothing').
I'll defo give these a try tomorrow (has been a long day tramping round moors and am super sleepy right now)! Fingers crossed and thanks for the help :)

---

