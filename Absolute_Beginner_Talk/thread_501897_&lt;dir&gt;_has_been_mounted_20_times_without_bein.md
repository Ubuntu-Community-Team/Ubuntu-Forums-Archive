---
title: "&lt;dir&gt; has been mounted 20 times without being checked"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by ResumeMan on 2007-07-15
What's that all about anyway? I haven't been able to check it in the documentation. What is it checking? Is it necessary? If not, can I get it to stop?

I tend to shut down the laptop everynight b/c the hibernate/suspend options don't work very well. So I'm getting this, which adds about 3-4 minutes to the boot time, semi-regularly.

Just trying to figure out what's going on...

---

### Post by southernman on 2007-07-15
It's just running a PMS file system check. You'll have to wait for someone else to tell you how to change the frequency of this happening. Better to have, than to have not. ;)

---

### Post by swoll1980 on 2007-07-15
pms a good thing? go figure

---

### Post by lisati on 2007-07-15
PMS = "Pretty Mean Sister". right?

The "mounted x times without being checked" is basically a safety feature.

---

### Post by confused57 on 2007-07-15
> **ResumeMan said:**
> What's that all about anyway? I haven't been able to check it in the documentation. What is it checking? Is it necessary? If not, can I get it to stop?

I tend to shut down the laptop everynight b/c the hibernate/suspend options don't work very well. So I'm getting this, which adds about 3-4 minutes to the boot time, semi-regularly.

Just trying to figure out what's going on...

Here you go:
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by pmg on 2007-07-16
I'll add that it's probably not a good idea to disable it altogether. If something bad happens and something corrupt gets writen, the sooner it's found the better the chances it can be fixed.  If you reboot frequently, or at verifying intervals, the **-i** option of **tune2fs** can be used to set the check frequency based on time since last check rather then number of mounts.

---

