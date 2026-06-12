---
title: "Error - artsmessage, cpu overload, aborting"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by gwilson on 2007-02-01
I've seen the following error message mentioned in at least one other posting, but I have not found an explanation or a response from anyone at Ubuntu:

Error - artsmessage    Sound server fatal error:  cpu overload, aborting

CPU usage would go up to about 100% and hang there. System never crashed.

I started seeing this on my last Edgy installation. I basically run a Gnome machine, but there are a few KDE apps that I really like, especially K3B. Unfortunately, I started getting that error after installing the KDE files needed to run things like Amarok and K3B, and now I am reluctant to install any KDE apps on my new install.

Anyone know what caused that error? Was it ever fixed or explained? I can post info on my system and chipsets, but I can't be the only one who ran into this.

Answers?

Glen

---

### Post by bustanil on 2007-02-01
I simply use **System Monitor** to stop **artsd** process. Run **Amarok** and change its **output plugin** configuration from **autodetect** to **esd.** I have to do this every time i want to hear music using amarok though :( . Nevertheless, it works and I prefer xmms rather than amarok :D . Any better idea?

---

