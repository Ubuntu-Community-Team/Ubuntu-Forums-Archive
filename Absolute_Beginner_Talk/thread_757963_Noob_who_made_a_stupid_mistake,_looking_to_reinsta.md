---
title: "Noob who made a stupid mistake, looking to reinstall"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by jofish15 on 2008-04-17
Ok, I'm dumb.  here's what I did:

I had previously installed Dapper Drake on one of my hard drives (I have XP on the other, w/ XP as the default).  From time to time I've fiddled with Ubuntu and I was trying to devote a little more time to it recently since I dread the Vista switch.  

One problem that I had with Ubuntu was that after switching to a new monitor (a 22" Hanns G), it didn't recognize my new monitor and kept the same crappy resolution as my old (5+ years) monitor.  So.... being the idiot that I am, I decided I was going to try and fix it.  Even though I know very little about programming and even less about Linux.  I followed the advice I found somewhere online - advice given to someone else - and tried to fix the x11/xorg.conf file via the terminal.  I can't stress how dumb that was.  I forget what exactly what I typed, but now when Ubuntu starts up I only get the terminal; no GUI.  

Since I didn't have very much data on that drive I was thinking about just reinstalling Ubuntu - a newer version.  So I burned an iso CD of Gusty Gibbon and tried to run the installation from that CD but it gets stuck on a monitor issue.  

Basically, what I'd like to do is reinstall Gusty Gibbon over my now screwed up version of Dapper Drake.  Any suggestions on the best way to do it?  Any help would be appreciated!

---

### Post by Tatty on 2008-04-17
You could try to fix your problem with your GUI by reconfiguring X:

```
sudo dpkg-reconfigure xserver-xorg
```

Since Hardy is out in 7 days, it might be easier to just fix your gui and update to hardy when it appears.

If you are sure you want to install Gutsy Gibbon, then you could always try the alternative CD - most problems installing with the Live CD are overcome with the alternative CD.

---

### Post by lamalex on 2008-04-17
A fresh install shouldn't be reading your old configuration file. Are you using the alternate cd or the livecd? Does the livecd load a desktop environment? I say download the alternate cd of Hardy Heron (which is released in 1 week) and install that. It has a lot of upgrades to X. If you want you can install the beta (which is quite stable, release candidate is out tomorrow), rather than waiting a week for the final release.

---

### Post by jofish15 on 2008-04-17
Is there any disadvantage to installing Gibbon now and upgrading to Heron when it comes out?  

And to answer a previous question, I was using the live cd.  

I think I'll try and fix the GUI tonight.  If that doesn't work, I'll try to install Gibbon with the alternative cd.  If fixing the GUI does work, I'll probably just wait for Heron and upgrade then.  

Thanks for the help guys!

---

### Post by bumanie on 2008-04-17
If you do a complete reinstall, I agree that hardy heron would likely be better than gutsy gibbon - I've used both. IMO hardy heron is by far superior.

---

### Post by jofish15 on 2008-04-18
Thanks for all the help guys.  I tried the 

sudo dpkg-reconfigure xserver-xorg

but it didn't work.  Taking your advice, I installed Heron w/ the alternate CD and it worked like a charm.  It recognizes my monitor and now I'm running Compiz in all its fine glory.  I was pretty much already sold on Linux, but now I'm absolutely sure - no Vista for me.

---

