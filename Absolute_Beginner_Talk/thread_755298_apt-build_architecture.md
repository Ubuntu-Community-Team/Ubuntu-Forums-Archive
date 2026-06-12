---
title: "apt-build architecture"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-04-14
When I installed apt-build, I was asked to select my architecture however, mine was not listed. I have an intel centrino duo. In the configuration file, what should I set it to?

---

### Post by bobplano on 2008-04-14
the architecture depends on what version of ubuntu you installed. there's x86(the 32-bit version), x64 (the 64-bit version) and a few others. a dual core processer like yours, can use 64-bits, but again, it depends on the version installed.

---

### Post by Inxsible on 2008-04-14
To get the architecture of your OS install you can type in```
uname -a
```

---

### Post by LK_gandalf_ on 2008-04-22
I have a Intel core 2 duo T7250 (Merom).
I don't know how to choose my architecture for apt-build, there are only few options about athlon cpu.

I have kubuntu 8.04 64bit

```
~$ uname -a
Linux doc-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```

Thank you for the help!

---

### Post by LK_gandalf_ on 2008-05-02
up

---

### Post by bobplano on 2008-05-02
the x86_64 means you have 64-bit OS installed, so go with the 64-bit architecture

---

