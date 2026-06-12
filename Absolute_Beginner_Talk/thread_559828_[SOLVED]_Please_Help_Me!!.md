---
title: "[SOLVED] Please Help Me!!"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by sasikirandadi on 2007-09-25
Why does the error "dependencies cannot be satisfied" comes?
I think the mistake i did is i installed edubuntu files as well as kubuntu files do to lack of proper knowledge about these things.
I have understood that its some display drivers problem regarding what to use?
Whether to use kdm/gdm?
Is there any solution for this?

---

### Post by skymera on 2007-09-25
that means you have broken packages.

the simplest way to do is

sudo apt-get upgrade -f

that should fix it

---

### Post by overdrank on 2007-09-25
> **sasikirandadi said:**
> Why does the error "dependencies cannot be satisfied" comes?
I think the mistake i did is i installed edubuntu files as well as kubuntu files do to lack of proper knowledge about these things.
I have understood that its some display drivers problem regarding what to use?
Whether to use kdm/gdm?
Is there any solution for this?

HI if you would like to remove kde or gnome you can try this link
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
And I believe the command that was reference is
```
sudo apt-get install -f
```

---

### Post by sasikirandadi on 2007-09-28
Thanks a lot! I could solve the problem!!!
UBUNTU ROX!:popcorn:

---

### Post by overdrank on 2007-09-28
> **sasikirandadi said:**
> Thanks a lot! I could solve the problem!!!
UBUNTU ROX!:popcorn:

Great glad to hear, good luck and could you mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

