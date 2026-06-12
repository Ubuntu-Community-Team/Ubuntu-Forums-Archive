---
title: "nautilus takes up 99% of cpu"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by ckamc on 2008-01-09
I tried searching to find out what it is but was unable to find a definate answer on what it is.

I am on 32bit 7.10 and right after watching a video I notice in my desklet that monitors my cpu that its running at 99~100%

most of it seems to be nautilus.

not sure whether to kill it (the process) or just to leave it be, I would like to fix it but I am unsure how to debug the issue.

is this something caused my the desklet/compiz/emerald?

---

### Post by RomeReactor on 2008-01-09
Hi. Open a terminal, and write or paste:
```
nautilus
```
If the CPU usage spikes again, see if Nautilus dumps messages in the terminal, and if so, please post them so we can take a look and help you figure out the problem.

---

### Post by ckamc on 2008-01-09
Straight from the dump file 

> ===== BEGIN MILESTONES =====
0x8177510 2008/01/09 18:10:19.8885 (USER): debug log dumped due to signal 11
0x8177510 2008/01/09 18:10:19.8966 (USER): debug log dumped due to signal 11
0x8177510 2008/01/09 18:10:19.8968 (USER): debug log dumped due to signal 11
0x8177510 2008/01/09 18:10:19.8969 (USER): debug log dumped due to signal 11
0x8177510 2008/01/09 18:10:19.8970 (USER): debug log dumped due to signal 11


and continues to do that but changing the time stamp

---

### Post by astoltz on 2008-01-09
It's a bug in nautilus: [https://bugs.launchpad.net/ubuntu/gutsy/+source/nautilus/+bug/150471]("https://bugs.launchpad.net/ubuntu/gutsy/+source/nautilus/+bug/150471")
Sounds like it's fixed in the next release, but not for Gutsy.  In the mean time, it's safe just to kill nautilus and then restart it.

---

### Post by ckamc on 2008-01-09
ahh ok

but what exactly does it do anyways? (the app/process)

---

### Post by frup on 2008-01-09
Nautilus is the file browser. Eg when you open a directory and look at it's contents the program you are using is nautilus.

---

### Post by BLTicklemonster on 2008-01-10
I'm seeing this, too. 

How does one go about killing and restarting nautilus, and can I make a launcher for it in case it happens again?

Thanks!

---

### Post by BLTicklemonster on 2008-01-10
What it trackerd? I just killed it and everything went back fine again.

ah looky

[http://ubuntuforums.org/showthread.php?t=591867](http://ubuntuforums.org/showthread.php?t=591867)

---

### Post by ckamc on 2008-01-10
yeah i saw that one right after i Killed nautilus, both being bugs now I could care less since I really do not notice much of a difference when i kill them

---

### Post by BLTicklemonster on 2008-01-10
I killed trackerd and my cpu has behaved rather nicely, so I removed it from sessions.

---

