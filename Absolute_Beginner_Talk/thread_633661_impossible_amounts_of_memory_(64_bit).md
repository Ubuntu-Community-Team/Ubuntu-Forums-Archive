---
title: "impossible amounts of memory (64 bit)"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2007-12-06
Check this out:

[IMG]http://i210.photobucket.com/albums/bb69/joentdothat/Screenshot-SystemMonitor.png[/IMG]

There's no way the memory count on that could be so high. And consistently that number. This must be a bug in the 64-bit version? Although apparently firefox takes up 0.1GB more than the rest with that impossible number. This is a clean, and relatively new install - so did 7.10 ship with this bug, if I'm right that that's what it is?

---

### Post by the.dark.lord on 2007-12-07
Looks like a bug, I've noticed the same problem. Here's my screenshot

[IMG]http://img466.imageshack.us/img466/235/screenshotsystemmonitorsj7.png[/IMG]

---

### Post by jordanmthomas on 2007-12-07
Interesting, what does this show?
```
free -m
``` and are the same numbers shown in top?

---

### Post by the.dark.lord on 2007-12-07
> **jordanmthomas said:**
> Interesting, what does this show?
```
free -m
``` and are the same numbers shown in top?

```
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           990        941         48          0         18        280
-/+ buffers/cache:        642        347
Swap:         2895          0       2895

```

---

### Post by jordanmthomas on 2007-12-07
> **the.dark.lord said:**
> ```
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           990        941         48          0         18        280
-/+ buffers/cache:        642        347
Swap:         2895          0       2895

```

Well, that looks perfectly normal, albeit a lot of used memory.
It appears it's just a bug with gnome-system-monitor.

---

### Post by the.dark.lord on 2007-12-07
I've filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/174611](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/174611)

---

### Post by jordanmthomas on 2007-12-07
Just so you know, you may want to update your screenshot for the bug report.  The one you posted doesn't have any memory numbers listed.

**edit** 
disregard that, it goes on to the right quite a ways.

---

### Post by the.dark.lord on 2007-12-07
> **jordanmthomas said:**
>  <snip>
disregard that, it goes on to the right quite a ways.

Ha, ha, I got a 21" monitor :)

---

### Post by misfitpierce on 2007-12-07
It's a bug when XGL or Compiz is enabled with system monitor.

---

### Post by the.dark.lord on 2007-12-07
> **misfitpierce said:**
> It's a bug when XGL or Compiz is enabled with system monitor.

Does not appear to be the cause of the problem.The problem is still there even when Compiz/Visual Effects are turned off.

---

### Post by jordanmthomas on 2007-12-07
But you are still running XGL, no?

---

### Post by hyper_ch on 2007-12-07
> **jordanmthomas said:**
> Well, that looks perfectly normal, albeit a lot of used memory.
Not-used memory is wasted memory ;)

---

### Post by jordanmthomas on 2007-12-07
> **hyper_ch said:**
> Not-used memory is wasted memory ;)
A lot of it was swap though.  :popcorn:

---

### Post by hyper_ch on 2007-12-07
swap wasn't used at all there ;)

---

### Post by jordanmthomas on 2007-12-07
Oh my.  To my defense, it was 5:15 a.m. when I posted that.  :P

---

### Post by stoodleysnow on 2007-12-07
It could be that Gnome-System Monitor has counted their memory usage as less than 0, and as such looped it back to the maximum number of Gigabytes allocatable with 64BIT? Reminds me of Y2K.:)

---

