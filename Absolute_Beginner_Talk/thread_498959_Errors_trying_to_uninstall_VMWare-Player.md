---
title: "Errors trying to uninstall VMWare-Player"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by ResumeMan on 2007-07-12
About a week ago I installed VMWare Player. I had some problems and decided to get rid of it. I tried to uninstall it thru either Add/Remove or Synaptic.

When I did I got the error message:

> E: vmware-player: subprocess pre-removal script returned error exit status 1

I checked the forums and saw a variety of command-line solutions. I tried (at least, I may be missing some):

> sudo apt-get remove vmware-player

> sudo apt-get purge vmware-player

> sudo apt-get remove --purge vmware-player

as well as their "aptitude" counterparts

> sudo rm -r /etc/vmware

and got errors each time. Somewhere in there I got a "broken package" message, and Add/Remove programs crashed when I tried to run it. I was able to clear that particular problem by re-running the uninstall in the command line.

Is there any other approach I can take? I'm getting this error even when I am installing or uninstalling unrelated packages! It doesn't seem to interfere with the installation of the other software, but it's certainly annoying.

I have (can re-create actually) much more detailed error messages if they'll help; didn't want to post long messages in this initial post in case I was missing something simple.

System: Feisty on a Toshiba A45 laptop, 512 MB RAM ~2.5 GHz, dual boot w/XP.

---

### Post by zvacet on 2007-07-12
```
cd /etc
```
```
sudo rm -r wmware
```

---

### Post by atria on 2007-07-12
Correction:
It should be 
```
sudo rm -r /etc/vmware
```

---

### Post by ResumeMan on 2007-07-13
> **atria said:**
> Correction:
It should be 
```
sudo rm -r /etc/vmware
```

Well the trouble is that having tried to uninstall, the folder etc/vmware isn't there anymore, so that command didn't work. But the computer still thinks there's some part of it there...so when I tried this command, I got a "not found" error, but I'm still getting the error message.

Any thoughts???

---

### Post by zvacet on 2007-07-13
```
whereis wmware
```

and you will see all directories with wmware files.Go to the everyone of them (cd /)and delete vmware files manualy.

---

### Post by RandyNose on 2007-07-31
Hey guys  I had the same problem.  I did a whereis, and deleted it, I think.  :)  

But still,  I'd like to be able to use some mapping / trip / route software, and I'm not aware of any that works for Linux. 

I installed wine, and the software installed fine. But now when I bring it up, it exits the program without my doing anything.  This is a major drag for us that need this kind of software.... (Truck Driver).  For most everything else, I could do away with XP....

---

### Post by anewguy on 2007-07-31
> **RandyNose said:**
> Hey guys  I had the same problem.  I did a whereis, and deleted it, I think.  :)  

But still,  I'd like to be able to use some mapping / trip / route software, and I'm not aware of any that works for Linux. 

I installed wine, and the software installed fine. But now when I bring it up, it exits the program without my doing anything.  This is a major drag for us that need this kind of software.... (Truck Driver).  For most everything else, I could do away with XP....

Try installing VMWare-Server - it's free and does a LOT more than player.  It requires a registration number that you get for free from the vmware site.  To install VMWare-Server, be sure the Ubuntu commercial repository is enabled in synaptic package manager, then just search for vmware and install server.  Much, much better.  Some people also like VirtualBox to do this as well.  It's personal choice - I just happen to like VMWare Server better!:)

---

