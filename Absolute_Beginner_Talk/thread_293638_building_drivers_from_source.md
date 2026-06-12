---
title: "building drivers from source"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by who_cares on 2006-11-05
I'm working on installing a Belkin USB wireless card (I hear that's not easy:( )

I downloaded the drivers for the Ralink chipset that is in the Belkin card from here:
[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

I cd'd into the directory and tried to run ./Configure
it displays:
```
 Linux kernel source directory [/usr/src/linux-2.6.17-10-generic]:
```

I have no idea what to type at that prompt.

Any ideas?

---

### Post by David_T on 2006-11-05
It looks like the ralink drivers are in apt.  
```

$ apt-cache search ralink
rt2400-source - RT2400 wireless network drivers source
rt2500-source - RT2500 wireless network drivers source
rt2570-source - RT2570 wireless network drivers source

```
I would make sure all your apt repositories are enabled (universe, multiverse, etc) in your /etc/apt/sources.list.  Then apt-get the one of these that applies to you, and then run sudo module-assistant, which will get the kernel headers for you and get everything set up.

---

### Post by who_cares on 2006-11-05
I need drivers for
Ralink RT2671F, RT2528L (RT73)

do you think the 2500 or 2570 would work for me?

---

### Post by who_cares on 2006-11-07
bump

---

### Post by FrodoB on 2006-11-09
See my reply to this post:

[http://www.ubuntuforums.org/showthread.php?t=296281&highlight=rt73](http://www.ubuntuforums.org/showthread.php?t=296281&highlight=rt73)

You are missing the kernel source, follow my response and you should get there.

---

### Post by who_cares on 2006-11-09
> **FrodoB said:**
> See my reply to this post:

[http://www.ubuntuforums.org/showthread.php?t=296281&highlight=rt73](http://www.ubuntuforums.org/showthread.php?t=296281&highlight=rt73)

You are missing the kernel source, follow my response and you should get there.

okay, I'll give this a shot and get back to y'all.

---

### Post by who_cares on 2006-11-28
> **FrodoB said:**
> See my reply to this post:

[http://www.ubuntuforums.org/showthread.php?t=296281&highlight=rt73](http://www.ubuntuforums.org/showthread.php?t=296281&highlight=rt73)

You are missing the kernel source, follow my response and you should get there.
okay, I gave that a shot
problem is when I got to step 10 the rt73.ko file didn't exist, but make never threw any errors that I noticed

any ideas?

---

