---
title: "winecfg problem, audio tab"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-11-06
Hello!

On winecfg, when I select the "audio" tab, winecfg crashes and I get the following error in the terminal:

```

amitroy5@Amit:~$ winecfg
libGL warning: 3D driver claims to not support visual 0x5b
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/amitroy5/.kde/socket-Amit.
can't create mcop directory
amitroy5@Amit:~$ 

```

Despite looking at other threads, I still am not able to fix this problem. How can I fix it? Thanks!

---

### Post by Paul_UK on 2006-11-06
I have the same problem (Ubuntu 6.10), so simply avoid clicking on it!  I don't use any audio apps in it anyway, so it's not a big deal.

I know that's no help at all - sorry.......

---

### Post by amitroy5 on 2006-11-06
Is this a bug in Ubuntu that everyone has? I had it on 2 machines. The exact same error.

---

### Post by bodhi.zazen on 2006-11-06
It is a bug with wine.

first use OSS over ALSA with wine.

Second you can try to downgrade you version of wine, change to OSS, and then re-upgrade.

See here: [Downgrade wine](http://doc.gwos.org/index.php/HowToWine#Downgrade_wine)

---

