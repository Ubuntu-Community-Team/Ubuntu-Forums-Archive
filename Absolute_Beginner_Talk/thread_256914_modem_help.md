---
title: "modem help"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-09-13
Hi, I was working on getting a driver for Ubuntu so that I could get my dial-up connection working, and I encountered a problem. I went through the hastle of downloading scanModem.gz and can't get past this point. I did the

```
cd ~/Desktop 
gunzip scanModem.gz
```


part of the process, but when I try to gunzip it, it says that scanModem.gz isn't in gunzip format. Any ideas? Thanks in advance!

---

### Post by Christopher Cook on 2006-09-13
Instead, in the terminal pppconfig works

---

### Post by blendmaster on 2006-09-13
I can't yet use pppconfig (I haven't gotten it installed yet) and I need a driver in order to use dial-up (I hate dial-up, but am living where I can't have broadband, wierd, I know). To find the driver, I need scanModem to tell me the information about my modem (and hopefully the site where I can download the driver for it).

---

### Post by blendmaster on 2006-09-13
Wait, do I need to first convert scanModem.gz to a different file format without uncompressing it? This is confusing me.

---

### Post by szf on 2006-09-13
> **blendmaster said:**
> Wait, do I need to first convert scanModem.gz to a different file format without uncompressing it? This is confusing me.

Open a terminal, change to the directory where you downloaded that file (i.e. ~/Desktop), then type in:

[FONT="Courier New"]$ file scanModem.gz[/FONT]

What does it tell you?

---

