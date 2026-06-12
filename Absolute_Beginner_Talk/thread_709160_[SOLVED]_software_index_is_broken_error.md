---
title: "[SOLVED] software index is broken error"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by mangurt on 2008-02-27
Greetings all,
I have a problem with synaptic.  I was installing java last night, and during the process, my son was kind enough to turn the power off to my system.  Now I get a message stating software index is broken.  Run sudo apt-get install -f to fix the problem.

Running that in terminal I get this result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin
The following NEW packages will be installed:
  sun-java6-bin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Any ideas on how to fix this?

Thanks.

---

### Post by erginemr on 2008-02-27
Perhaps deleting the offending lock file can help:
```
sudo rm /var/cache/apt/archives/lock
```

---

### Post by mangurt on 2008-02-27
Thanks for the response.

I am sorta nervous about deleting something like that.  I read that the -rm command can really screw stuff up.

I'm willing to try that, but I wonder if there are any other suggestions?

---

### Post by kellemes on 2008-02-27
> **mangurt said:**
> Thanks for the response.

I am sorta nervous about deleting something like that.  I read that the -rm command can really screw stuff up.

I'm willing to try that, but I wonder if there are any other suggestions?
Check if Synaptic or the Update Manager are open and locking apt.

```

ps -A | grep apt
ps -A | grep update

```

If so.. kill those applications/daemons.

---

### Post by kpkeerthi on 2008-02-27
Do you have more than one package manager running at the same time? You can't have synaptic and apt-get running at the same time as the lock file will prevent the other one from running. 
It is safe to delete this file if you are sure that no package managers are running. 
If you are still paranoid, a reboot should sort it out.

---

### Post by mangurt on 2008-02-27
I don't know if I am paranoid per say...I just want to make sure I am not doing something that will completely kill my computer.

As for having other managers running, I noticed that I had the icon in the upper right hand corner stating that I have updates.  That's the only thing that is running.

---

### Post by mangurt on 2008-02-27
> **erginemr said:**
> Perhaps deleting the offending lock file can help:
```
sudo rm /var/cache/apt/archives/lock
```

Well, that did the trick!  Thanks!

---

