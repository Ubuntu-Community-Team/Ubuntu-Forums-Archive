---
title: "[SOLVED] Did anybody have time synch problem?"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by incen on 2008-03-14
Hi, after changing into daylight saving time, the time on my Ubuntu seems messed up!
I have ntp installed, select 'keep synchronized with Internet server', and pick up American/New York. It should be fine! Right? But now it's still 8 minutes late. Kinda annoying. Can anyone help me to figure this out? Thanks a ton!

---

### Post by glennric on 2008-03-14
Try to change the configuration to "Manual" and select "Synchronize Now".  Then change it back to "Keep synchronized..."  Then wait a bit and see if your clock adjusts.  You could also try changing the server that your computer synchronizes with.

---

### Post by incen on 2008-03-14
Thanks. It works! :)

---

### Post by jrickard on 2008-04-03
What's solved.  Yes, this works.  But for the past month, my clock keeps wandering off into the woods.  I have it set to stay synched, but have to go manual about once a day.  

Is anybody else having clock problems?

I'm quite often off by as much as 90 minutes PER DAY.

Jack Rickard

---

### Post by epeeist01 on 2008-04-05
> **jrickard said:**
> What's solved.  Yes, this works.  But for the past month, my clock keeps wandering off into the woods.  I have it set to stay synched, but have to go manual about once a day.  

Is anybody else having clock problems?

I'm quite often off by as much as 90 minutes PER DAY.

Jack Rickard

Sounds like it may be time for a new crystal for your motherboard RTC?

---

