---
title: "How do checks on remaining hard disk space work?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by felicity on 2007-06-21
My question refers to conky, but I believe it's more general to other software in linux. 

I use conky to check and display the remaining disk space on my hard drives. 

But how exactly does it go about gathering that information? 

That is, does it constantly read from the drives each time it checks (every few seconds), and if so, can this reduce the life-span of my hard drives? :-k

Also, a few of my drives are used for storage and hardly accessed often. Would they normally be put to sleep if they haven't been accessed for a certain period of time, or are they constantly spinning anyway? :-k

---

### Post by p_quarles on 2007-06-21
I don't use the application you're referring to, but my guess is that it only updates the free space after the drive has been accessed by another process. If you're worried, though, you can always just use the handy CLI version:
```
df -h
```

---

### Post by felicity on 2007-06-22
p_quarles: Thanks for your help!

---

