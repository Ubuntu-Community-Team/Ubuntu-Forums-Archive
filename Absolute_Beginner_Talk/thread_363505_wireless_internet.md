---
title: "wireless internet"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-17
I recently just started with ubuntu and am having problems with wireless internet. I cannot get ubuntu to detect my wireless card and also I cannot find any program for detecting wireless connections. I would greatly appreciate any help you can give me for having ubuntu detect my wireless card and connecting to my wireless network. Thank you.

:KS :)

---

### Post by pebo on 2007-02-17
Post the output of these commands:```
 lspci | grep Network
``````
ifconfig -a
```

---

### Post by lien_meat on 2007-02-17
It would be nice to know information about which wireless card you have.
However, I'm guessing since your wireless wasn't detected you MIGHT need to try out NDISWRAPPER.  There are some good tutorials on this forum that helped me out if you find that your card isn't supported automatically in linux.

---

### Post by happy-and-lost on 2007-02-17
wifi-radar (It's in the repos) is a great GUI for connecting to wireless networks, provided you've got your card working.

---

