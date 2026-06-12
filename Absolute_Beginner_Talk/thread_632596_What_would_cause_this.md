---
title: "What would cause this?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-05
How do i fix this?  
Insane boot time.
Only happens once in a while, but i dont know what it is.
Thanks.

---

### Post by vikram on 2007-12-05
nothing to fix. every 60 days or so your partitions will be checked for errors. dont worry about it.

---

### Post by jasmuz on 2007-12-05
Its not ever&#285; 60 days or so.. its 30 boots.
You could modify that by tweaking with the config file that controls the ext3 checkup.

---

### Post by jordank on 2007-12-05
but it seems to happen much more frequently than that. and my screen is black for the whole time while it's happening. i've seen it do the partition check, but i dont think that this boot was it. usually it shows it's progress, etc.  this time the screen was just black.

---

### Post by Dr Small on 2007-12-05
> **jasmuz said:**
> Its not ever&#285; 60 days or so.. its 30 boots.
You could modify that by tweaking with the config file that controls the ext3 checkup.
I was going to say that... Because if you leave you system up for 60 days, it isn't going to shutdown just to run fsck. Anyhow, yeah, It's every 30 boots by default.

---

### Post by Steveway on 2007-12-05
If that happens again, wait till it it has booted, open a terminal and type "dmesg" into it. (Without the Quotes "")
Then post the Output here.

---

