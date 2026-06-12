---
title: "/dev/sda8"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-11
when i boot from the last two days say once out of 4 times i get an message before starting up that says
```
/dev/sda8 has be mounted 33 times without check check enforced
```
and a checking continues and everything then happens normally .Is something terribly wrong

---

### Post by Outrunner on 2007-06-11
Perfectly normal.

---

### Post by Soybean on 2007-06-11
Just to make sure I understand what you're saying... you booted your computer 4 times, and this happened once? If so, that's normal. :) If you mean that you booted many times, and this happened every 4th time, that's a little weird.

Your system is set up so that every once in a while, it checks the hard drive for errors. This check can only be done while nothing else is using the drive, so it's easiest to do it during the boot process, before everything else has started. I'm not actually sure how it decides how often to check, but I believe it's configurable. You'll probably notice a similar check happening if your computer is ever shut down suddenly without going through the shutdown process (e.g. due to a power failure).

---

### Post by pardesi on 2007-06-11
no 1/4 was just an approximation ...if thsi was normal thanks:p

---

### Post by Cypher on 2007-06-11
During the EXT3 filesystem creation, a default number is chosen for the number of the times the partition can be mounted without being checked as long as the system was shutdown properly.

If you type
```

sudo tune2fs -l /dev/sda8

```
you'll get a bunch of information including things like, "Mount Count", "Check Interval". These things determine when the check should happen.

Now if /dev/sda8 is a harddrive partition, it should only be mounted once during each boot. That being said, the filesystem shouly only be checked once every approx. 30 boot-ups. Not one in 4 or whatever you are seeing.

---

