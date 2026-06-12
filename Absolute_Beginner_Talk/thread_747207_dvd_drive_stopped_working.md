---
title: "dvd drive stopped working"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by spookyct on 2008-04-06
Hey Guys,

My DVD-R drive just stopped working the other day.  The lights come on and stuff, but it is not reading CDs in ubuntu.  As a check, I re-booted the machine with the live CD in the drive, and there were no errors.  This leads me to believe that the drive is still good.

Is there an *ubuntu* way of diagnosing this problem?  I don't really know my way around configuration files.

---

### Post by mick8985 on 2008-04-06
Put a cd in and type this into the command line
```
sudo mount /media/cdrom0
```
What does it say?

Could you perhaps have disabled automounting? I know if you run powertop it will try to do this to save power.

---

