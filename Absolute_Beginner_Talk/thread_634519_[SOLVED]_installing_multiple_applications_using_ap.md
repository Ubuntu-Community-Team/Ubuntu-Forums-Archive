---
title: "[SOLVED] installing multiple applications using aptitude"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by mdpalow on 2007-12-07
Can you install multiple applications in one command line using aptitude? If so, what is the separator between the apps?

example:

sudo aptitude install k3b,k9copy,devede

that doesn't work by the way; tried it.

Also, when using synaptic to install something, you aren't asked to enter 'Y' if you want to do it, it just installs everything once you tell it to begin. Why when you enter the 'aptitude install' command in the terminal it will ask you if you want to continue and to press 'Y' ??

Can you get around that and just have terminal install without stopping?

Thanks...

---

### Post by taurus on 2007-12-07
Don't include the commas in there.  An empty space would do just fine.

```
sudo aptitude update
sudo aptitude install k3b k9copy devede
```

---

### Post by mdpalow on 2007-12-07
Geez... I'm always having to put something in between that it doesn't even occur to me to  leave it with only a space.

That did it... thanks very much taurus

anyone know the answer to my second question??

---

### Post by taurus on 2007-12-07
When you put a check mark to install let's say k3b under synaptic, it will tell you that you need to install a bunch of dependencies to satisfy it.  It gives you an option to either except those dependencies or not.  So, as you can see, it's just like you would have seen from a terminal if you install k3b with apt-get.

---

### Post by mdpalow on 2007-12-07
oh, so it's the dependencies that you are being asked about and not the original app.

---

