---
title: "Kde uses over 700mb ram??"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-10-16
I have a memory moniter (karamba theme) telling me i have ver 700 mb memory. Besides that number, Im getting high numbers on used memory in both that theme and ksysguard. I know its really not using that much memory so is there an explaination :S??

---

### Post by Bree on 2006-10-16
Are you sure it's not being cached? What's the output of free -m in Konsole?

---

### Post by aysiu on 2006-10-16
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by TheWizzard on 2006-10-16
if you want graphical feedback, you can take a look at 'memory' in the KInfoCenter

---

### Post by Madpilot on 2006-10-16
Linux will use as much memory as it can find, to get the system running faster by caching as much stuff as possible.

I've got 1Gb of RAM; I frequently run at 80-90% usage, but most of that (40-60%) is cache.

As the link that aysiu provided said, "the RAM is wasted if it isn't used".

---

### Post by mips on 2006-10-16
It's probably cached which is a bit confusing to a someone new to linux. I would not worry about it to much.

I'm using about 800MB of 1GB but a lot of that is cached.

---

### Post by WalmartSniperLX on 2006-10-16
> **Bree said:**
> Are you sure it's not being cached? What's the output of free -m in Konsole?

ahh I see. It says 844mb used, 578 cache. 

Thanks for the help everyone :D I understand now

---

