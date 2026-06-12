---
title: "GTKpod"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by NADIASOSA on 2005-12-18
Hi All,

As many of you, I am a new user. Although I've had different linux distributions in the past I consider myself a dummie. :rolleyes: 

I have setup and running Gtkpod (luckily it came already installed with my distribution). After solving a few errors I encountered while connecting my ipod here is one, that I can not find any help on the other threads I've read. Please help!

iPod directory structure must be present before synching to the iPod can be performed.


This error shows when I'm trying to sync the music into the ipod. when I try doing Create Ipod directories, I get an error as well.

Can somebody be kind enough to explain, in simple words, for a dummie like me, what's wrong?

Thanks!

Nannys

---

### Post by eudemon on 2005-12-19
Have you checked to make sure you have permissions to write to the directory where gtkpod is trying to create the directory structure?  Default permissions on my ipod prevented me from creating the directory structure until I a chown on the iPod_Control directory.

---

### Post by hanzj on 2006-08-03
```
sudo chown hanzj /media/ipod

```
I did the above, and i don't get the Warning message anymore, but no synching seems to be taking place when i press sync.

---

