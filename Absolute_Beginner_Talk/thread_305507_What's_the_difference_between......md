---
title: "What's the difference between....."
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-23
I feel really stupid for not knowing this yet after using Ubuntu for about two months. But I still have no clue what the difference between "aptitude" and "apt-get" is. I really don't feel like reading thirty pages worth of stuff just to figure this out, so I came here hoping to get some answers.

---

### Post by taurus on 2006-11-23
Almost the same except aptitude can handle dependencies better.  For instance, if you plan to install KDE, you would use aptitude so that when you decide to remove KDE later, aptitude can remove all the dependencies that came with it when you first installed it.  Apt-get might leave some orphan files around the system, taking up space...

---

### Post by voodoonirvana on 2006-11-23
> **taurus said:**
> Almost the same except aptitude can handle dependencies better.  For instance, if you plan to install KDE, you would use aptitude so that when you decide to remove KDE later, aptitude can remove all the dependencies that came with it when you first installed it.  Apt-get might leave some orphan files around the system, taking up space...

So would it generally be better to use "aptitude" from now on? What was the point in creating "apt-get" in the first pllace if aptitude did just fine?

---

### Post by taurus on 2006-11-23
Okay, here is something for you to read...

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

It's like different strokes for different folks...

---

