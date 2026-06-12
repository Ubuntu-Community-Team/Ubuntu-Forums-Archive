---
title: "Power Mac G5 dual 2.7 (WC) Fan racing?"
date: 2009-02-18
forum: Apple Hardware Users
---

### Post by dpole on 2009-02-18
Hi all,

Have just installed edubuntu 6.06 LTS, (will install 7.10 later having just found the link to the iso, from your forum Doh!).

the major problem i have so far is a racing fan, in fact, all the fans kick in and race flat out even at low or no load, the noise is intolerable!

any one point me in the direction of a cure? in OSX land i could at least select preferences>power saving and have the option Automatic/full/low 

on auto and full the fans operated intermittently, on low the fans hardly ever cut in...

Is there a way of tweaking the Open Firmware? is there a process to control fan operation?

please save my sanity, earmuffs are not an option...:D

---

### Post by tiresia on 2009-02-18
First of all, on your machine you can run Ubuntu Hardy or Ubuntu Intrepid.
You can download them here
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
I had problem with fans by using the alternate CD. Therefore the best solution I suggest you, is to use the Desktop Ubuntu Hardy (8.04.1). By the way, it is a wonderful tool, to rescue your computer from any problems you can have.

After that you can upgrade Hardy to Intrepid, if you prefer.

Anyway, if you still have problems with the fans, try powernowd (a daemon for userspace, the scaling governor - it should be installed by default in hardy) or alternatevely cpudyn. Find, what is the best solution for you.
Here some infos 
[http://ubuntuforums.org/showthread.php?t=994774&highlight=powernowd](http://ubuntuforums.org/showthread.php?t=994774&highlight=powernowd)

---

### Post by dpole on 2009-02-18
> **tiresia said:**
> First of all, on your machine you can run Ubuntu Hardy or Ubuntu Intrepid.
Anyway, if you still have problems with the fans, try powernowd (a daemon for userspace, the scaling governor - it should be installed by default in hardy) or alternatevely cpudyn. Find, what is the best solution for you.


Thanks for the links, both options seem ok i think cpudyn seems best..

im intending, for my sins to run an LTSP, and would prefer to have precompiled server client set up, though im still scratching my head, how to set up the G4 imac, perhaps a second ethernet, on the server side might speed things along..:D

---

### Post by tiresia on 2009-02-18
> **dpole said:**
> Thanks for the links, both options seem ok i think cpudyn seems best..
Well, not always. You can just try both. Cpudyn is more 'flexible' and will switch among the cpu governors fast - but therefore it can be annoying with the fans...
You can maybe find also cpufrequtils interesting (if you want to set yourself the speed - [http://www.thinkwiki.org/wiki/How_to_use_cpufrequtils](http://www.thinkwiki.org/wiki/How_to_use_cpufrequtils)) or use the 'cpu frequency scaling monitor' of gnome to control yourself the cpu's speed (but it is not always advisable).
For the last (GUI) solutions, first add them to a panel (right click to a panel) and then run:
```
sudo dpkg-reconfigure gnome-applets
``` 
Now you can just choose the governor you want to use according to your needs

---

