---
title: "New ubuntu user...HELP!!!"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by jeff_flynn on 2008-01-23
I have ubuntu 7.10 - the Gutsy Gibbon

My old Operating System was Windows XP Home Edition, but a virus killed the computer, so i took it into the shop, they said it was toast so they installed Linux ubuntu 7.10 - the Gutsy Gibbon, and i don't know how to install the Java i need in order to play RuneScape....help!!

thanks

---

### Post by Sinkingships7 on 2008-01-23
i have a similar issue. the same one, actually, only i play pogo ^_^

---

### Post by Arthur Archnix on 2008-01-23
```
sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-plugin
```

That should install everything you need. Run it from a terminal.

EDITED

---

### Post by jeff_flynn on 2008-01-23
I did that, then this came up.....

====================================
Ubuntu@ubuntu:-$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sun-java6-plugin
Ubuntu@ubuntu:-$
====================================

---

### Post by Arthur Archnix on 2008-01-23
Hmm... must be in a different repository. 
```
gksudo gedit /etc/apt/sources.list
```
Uncomment (remove the #) from in front of the community, partner, universe & multiverse lines. **If something says src or backports, leave that commented**. When done, save, close. Then do this:
```
sudo apt-get update
```
Then try those commands above again. I just ran them myself, and found I had to install the jre first, then the plugin. Edited to reflect that.

---

### Post by macogw on 2008-01-23
> **Arthur Archnix said:**
> If something says src or backports, leave that commented
It's fine to uncomment those.  src just means that if you *want* to download a source package and look at the code, you can easily do it from the repositories.  If that's uncommented and you never download a source package from apt, it doesn't make a difference at all.  Backports is also fine to uncomment.  Backports just gets you new versions of software that have been backported from newer versions of Ubuntu, since the regular repositories don't upgrade the desktop applications unless it's to fix a security hole.  If you want something new for the new functionality, the way to get it is backports.


The non-command line way to do all this:
System -> Administration -> Software Sources
check them all off
System -> Administration -> Synaptic Package Manager
Reload the package lists (the button's in the top left), then if you just click on the column where all the names of the packages and start typing "java" it'll jump down to those and you can check them off.

---

