---
title: "Installed Kubuntu, Partitioned 13GB of HDD"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Arcturus on 2007-01-14
I've installed Kubuntu on my machine. I'm now running a dual boot system.

I only partitioned 13GB of my HDD for Kubuntu. After playing with Kubuntu for some time, I log back into XP and notice that my HDD appears to have 86GB on it. My HDD is 160GB... What exactly went wrong? :confused:

I'm probably going to have to reformat my HDD...

---

### Post by louieb on 2007-01-14
Lets see what is going on. Open Applications>Accessories>Terminal and run
```
sudo fdisk -l
```that a small l as in little.
and copy and past  output here.
and while your at it do the same with 
```
df -Th 
```

---

### Post by marx2k on 2007-01-14
Also, you can get a visual handle on things by starting up gparted either through the liveCD or from your Ubuntu Installation (if not installed, in a terminal type 'sudo aptitude install gparted')

---

