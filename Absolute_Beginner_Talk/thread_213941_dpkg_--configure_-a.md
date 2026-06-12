---
title: "dpkg --configure -a"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Ulysses on 2006-07-12
Hello

I installed 5.10 and downloaded the 163 upgrades
Haven't gone to 6.06 yet because the 3 times before on my desktop, it crashed.
But in the middle of the upgrades it froze. I shutdown. Restarted. And it worked pretty much okay. But I got this error message and when I tried to run it in terminal I got an error message telling me that I needed to be a superuser.

dpkg --configure -a

Can someone please help? Does this mean I have to start all over? Again?

RAR

---

### Post by SigmaX on 2006-07-12
It's asking you to run the command "dpkg --configure -a" isn't it?  You have to run it as a superuser, which, in Ubuntu, means using sudo:

```
sudo dpkg --configure -a
```

It will ask you for your password, which is a normal security process to keep people with admin rights from accidentally messing things up.

> **Ulysses said:**
> Does this mean I have to start all over? Again?


Heh; In Linux you almost never *have* to completely "start all over," it can almost always be fixed if you know what you're doing.  But often reinstalling is the quickest and easiest way to solve an issue if you don't know the technicals involved.

SigmaX

---

### Post by Dr. Nick on 2006-07-12
Running sudo dpkg --configure -a will save you from starting over. It just means that it was interrupted last time and needs to finish before proceding. That command will just pick up where it left off

---

