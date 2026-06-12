---
title: "Computer won't restart - general non-Windows question"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2007-12-11
I've got an old computer, originally packaged with Millennium, that I have put Xubuntu 7.04 onto.  I can shut the computer down, but I can't do a restart - when I restart, the reboot hangs on the opening page - in this case one showing the Gateway logo.  All options on the logo, such as F2, are non-function when in this state.  This is not a specific problem to Xubuntu - it also happened when I installed Puppy Linux onto it.

I checked the Netbios settings, and there doesn't seem to be much I can alter.  There doesn't even seem to be an option to change the boot device order.  

So I'm assuming, when I removed windows, and FDisked everything (including FDisk /MBR) that I removed some application that facilitated restart.

So any ideas?  It's not a major problem, just an annoyance.

---

### Post by HermanAB on 2007-12-11
No restart, but since you are talking about shutting down, I'm assuming you can do a cold start.

Restart issues are frequently power supply related.  Something needs to have its power cycled in order to wake up and run properly.  This is frequently the ethernet controller.  There is nothing much you can do about it.  

In any case, you should not need to restart more than about once a year when you upgrade the system to the next version of Ubuntu, so this should not be much of a problem!

Cheers,

H.

---

### Post by forestpixie on 2007-12-11
I had a similar problem - owuldn't restart with any distro I had a look at - either installed or running as a livecd - until I installed Gutsy and now it works

---

### Post by getmeoutofhere on 2007-12-11
Thanks for the replies.  The restart was working find when it had Me on it, and I don't have an ethernet cable on the computer - it connects to the internet via USB wireless.  Wouldn't know about Xubuntu 7.10, because it won't run on this computer - unusably slow.

---

