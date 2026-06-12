---
title: "Rar?!"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by flaak_monkey on 2006-05-21
How do you unRAR things in LINUX? Or can you?

---

### Post by bluevoodoo1 on 2006-05-21
with the "unrar," "unrar-free" or "unrar-nonfree" packages. Should be in synaptic. I have the last two packages installed.

---

### Post by flaak_monkey on 2006-05-21
i do not see those packages anywhere.

---

### Post by bluevoodoo1 on 2006-05-21
I believe one is in the universe and one is in multiverse.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by it.henrik on 2006-05-21
hmm .. have you added all the extra repositories?

[https://wiki.ubuntu.com/AddingRepositoriesHowto#head-3af7264a0e97edbc5bf039e5bdb971f46c43269a](https://wiki.ubuntu.com/AddingRepositoriesHowto#head-3af7264a0e97edbc5bf039e5bdb971f46c43269a)

---

### Post by glotz on 2006-05-21
Here's something [http://packages.debian.org/unstable/utils/unrar](http://packages.debian.org/unstable/utils/unrar)

---

### Post by mlind on 2006-05-21
```

$ apt-cache policy unrar
unrar:
  Installed: 1:3.5.4-0.1
  Candidate: 1:3.5.4-0.1
  Version table:
 *** 1:3.5.4-0.1 0
        500 http://fi.archive.ubuntu.com dapper/multiverse Packages
        100 /var/lib/dpkg/status

```

on multiverse it seems. unpack using *unrar e package*.
*file-roller package* works too.

---

### Post by flaak_monkey on 2006-05-21
i did not have the respotories. but i do now, and found it. ty. :P

---

### Post by bluevoodoo1 on 2006-05-21
[QUOTE=flaak_monkey]i did not have the respotories. but i do now, and found it. ty. :P[/QUOTE]

Ok. And it's working right?

---

