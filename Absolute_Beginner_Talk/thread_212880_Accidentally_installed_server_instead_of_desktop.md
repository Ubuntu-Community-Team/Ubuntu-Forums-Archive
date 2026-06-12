---
title: "Accidentally installed server instead of desktop"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by zane on 2006-07-10
Hello everyone... I am new to Linux and accidentally installed the server version of linux instead of the desktop(I want to run xp and ubuntu desktop).  I knew that I wanted to install ubuntu permanently onto my computer so I thought that I wanted this version instead of the live cd version.  Are there commands I can use to install the desktop version or should I repartition and then reinstall the desktop version?

---

### Post by aysiu on 2006-07-10
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by mostwanted on 2006-07-10
Insert your install CD and run this command:

sudo aptitude install ubuntu-desktop

---

### Post by az on 2006-07-10
sudo apt-get install ubuntu-desktop linux-386

and you are good to go.

You can install linux-686 if you have a pentium or linux-k7 if you have an AMD CPU.

You need to install the desktop kernel since the server kernel often does not play nice with doodads...  (linux-386, linux-686 linux-k7 are all desktop kernels)

---

### Post by aysiu on 2006-07-10
That's true if zane downloaded the Server CD (which I think is what probably happened).

Interestingly enough, though, it isn't true if it's a server install from the Alternate CD.

---

### Post by Brain Juice on 2006-07-10
would one lose their /home data doing this?

---

### Post by aysiu on 2006-07-10
> **Brain Juice said:**
> would one lose their /home data doing this?
No, you won't lose any data.

---

