---
title: "problem with su"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by sailen on 2006-01-27
I've installed Kubuntu 5.10 on the system. The comp is AMD Athlon 1.8, Asus A7V333, 768M DDR, Radeon 9600pro, have no net adapter.
After installation I wanted to configure servises. Suddenly su and sudo started bugging. 
For example I start Kuser, type password, then it says "su retuned with an error" some programs says "conversation with su failed"
sudo even doesn't respond.
Who know what's the problem about?

---

### Post by Adrian on 2006-01-27
[QUOTE=sailen]I've installed Kubuntu 5.10 on the system. The comp is AMD Athlon 1.8, Asus A7V333, 768M DDR, Radeon 9600pro, have no net adapter.
After installation I wanted to configure servises. Suddenly su and sudo started bugging. 
For example I start Kuser, type password, then it says "su retuned with an error" some programs says "conversation with su failed"
sudo even doesn't respond.
Who know what's the problem about?[/QUOTE]

Instead of using **sudo** to start KDE applications, try using **kdesu** instead.

---

### Post by Madpilot on 2006-01-27
Also, have a read of [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) if you haven't already, it does a good job of explaining how (K)Ubuntu handles sudo/root/etc...

---

