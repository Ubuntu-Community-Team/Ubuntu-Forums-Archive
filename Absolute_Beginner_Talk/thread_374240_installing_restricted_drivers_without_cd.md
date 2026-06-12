---
title: "installing restricted drivers without cd?"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by ELD on 2007-03-02
is there a way, evertime i try in synaptic it just asks me to put in cd, i dont have a cd and i dont want to download 600mb+ just for the restricted stuff :(

---

### Post by Maestro23 on 2007-03-02
> **ELD said:**
> is there a way, evertime i try in synaptic it just asks me to put in cd, i dont have a cd and i dont want to download 600mb+ just for the restricted stuff :(

In terminal you can search/list just restricted:

> apt-cache search restricted

See what you need and install.  Can do the same in Synaptic.  Just search "restricted".

I'm sure there is another way, I just tried this when I saw your post.

Good luck.

---

### Post by ELD on 2007-03-02
Well i try to install linux-generic from restricted, it adds a few more packags, i do ok and then it wants the dam cd, wtf!

---

### Post by mcduck on 2007-03-02
run 'gksudo gedit /etc/apt/sources.list' and put a # in front of the first line about cdrom. This disables using the ubuntu CD to install packages, and now everything is downloaded from the Internet instead.

---

### Post by ELD on 2007-03-02
Your a bloody star mate!

---

