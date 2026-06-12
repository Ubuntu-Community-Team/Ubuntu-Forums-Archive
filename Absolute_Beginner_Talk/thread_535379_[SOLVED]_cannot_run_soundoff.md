---
title: "[SOLVED] cannot run soundoff"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by johnapeterson on 2007-08-26
Hello,

I am trying to run the soundoff command, when I do I get this message:


john@john-desktop:~$ sudo soundoff

Some applications are still using OSS - cannot unload

5623 /usr/bin/esd-terminate-nobeeps-as1-spawnfd24

Please stop these applications and run soundoff again


I cannot find where this app is running and how to stop is.  Looking at the system monitor, I do not see any processes running that would require sound.

I am a newbie, so I might need step by step.

Thanks,
John

---

### Post by ddrichardson on 2007-08-27
If you need to kill that app then you use```
kill -9 pid
```Where pid is the number given by sudo soundoff - i.e. 5623.

This number changes everytime the program is run, but```
ps -a|grep esd
```will get you the new one.

---

