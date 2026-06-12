---
title: "Hard drive access diagnostics?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-10
My laptop hard drive spins up every 5 seconds or so, and I don't know why. If I'm doing something like typing or scrolling through a list, it freezes for a half second. How do I find out what is being accessed, and how do I make it stop it? (While typing, the characters stop displaying during this time, and catch up when it is done. Rather irritating...)

---

### Post by dcstar on 2008-01-10
> **imaginal said:**
> My laptop hard drive spins up every 5 seconds or so, and I don't know why. If I'm doing something like typing or scrolling through a list, it freezes for a half second. How do I find out what is being accessed, and how do I make it stop it? (While typing, the characters stop displaying during this time, and catch up when it is done. Rather irritating...)

When Ubuntu detects that you have a laptop it sets the hard disk(s) to minimum power consumption, sometimes these commands can cause problems if the particular hard drive interprets the command in an unexpected way (and goes into "Standby" mode too early).

The file /etc/acpi/power.sh contains the relevant commands and /etc/default/acpi-support contains the settings you can change.

Open a terminal and do this to see the commands you can use to check/set these things:
```
man hdparm
```

You can also install the** smartmontools** package to test your drive.

---

### Post by jeffus_il on 2008-01-10
> **imaginal said:**
> My laptop hard drive spins up every 5 seconds or so, and I don't know why. If I'm doing something like typing or scrolling through a list, it freezes for a half second. How do I find out what is being accessed, and how do I make it stop it? (While typing, the characters stop displaying during this time, and catch up when it is done. Rather irritating...)

There are a number of threads on this problem, something connected to a sata bug.
Do a search.

---

### Post by imaginal on 2008-01-10
There are a ton of links on this, but being new, I just thought it was something I was doing. I was using the wrong search phrases here because I didn't know what I was looking for. Future reference, here are the important links.

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695")
[http://ubuntuforums.org/showthread.php?t=591503]("http://ubuntuforums.org/showthread.php?t=591503")

---

