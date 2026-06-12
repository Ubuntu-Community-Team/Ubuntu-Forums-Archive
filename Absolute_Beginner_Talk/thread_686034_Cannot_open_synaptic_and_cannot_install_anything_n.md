---
title: "Cannot open synaptic and cannot install anything now."
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by tel93 on 2008-02-02
When I was in the middle of installing sun-java6-jre my gay little brother pulled out the power and the install failed. When I rebooted and opened synaptic it had an error saying:

[img]http://img138.imageshack.us/img138/337/screenshotsynapticrd4.png[/img]

I tried that in the terminal but it says I need to be a superuser. GAAHHHHH! )(*^%)^$#

In my dpkg.log:

2008-02-03 11:56:14 install sun-java6-bin <none> 6-03-0ubuntu2
2008-02-03 11:56:14 status half-installed sun-java6-bin 6-03-0ubuntu2

---

### Post by Rocket2DMn on 2008-02-02
You need to use sudo
```
sudo dpkg --configure -a
```

---

### Post by Sammi on 2008-02-02
Read a few lines of this document, and you'll learn a bit about superuser privileges and the sudo command in Ubuntu: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

