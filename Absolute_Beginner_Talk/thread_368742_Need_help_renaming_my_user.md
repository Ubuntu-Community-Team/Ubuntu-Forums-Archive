---
title: "Need help renaming my user"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Iceni on 2007-02-23
Hi. I'll start out with the usual I'm completely new warning. I installed ubuntu, and got most things like the nvidia driver working. However, I have two problems:

1. I can't access users and groups. I've looked around the forums, and I found out that the problem is related to the real name I used when installing. I have a weird character in my name (é) and ubuntu don't like it. So, how do I change the real name I used?

2. This might be related to the first problem. When i pico edit xorg.conf or other files in the terminal It won't let me save, it said permission denied. How do I fix this?

Thanks in advance for all help:)

---

### Post by po0f on 2007-02-23
Iceni,

I don't have a clue about a solution to your first problem, but the second one is easy enough to fix.  Prefix "sudo" to your commands to have them run with root access:

```
[font="Courier New"]$ sudo pico /etc/X11/xorg.conf[/font]
```

---

