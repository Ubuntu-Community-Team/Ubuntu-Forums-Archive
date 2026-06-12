---
title: "please tell me what key board conf your mac (notebook) uses"
date: 2017-03-01
forum: Apple Hardware Users
---

### Post by jeff666 on 2017-03-01
i was being lazy when i installed and didn't check my F keys which don't work. This is my /etc/default/keyboard file:

```
# KEYBOARD CONFIGURATION FILE
# Consult the keyboard(5) manual page.
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""
BACKSPACE="guess"
```

just wondering if you could check and see if your F keys work and if your files any different thanks. Or if there is some other way i can get them working! I also ran 'sudo lshw' but not sure which is the key board and don't think its driver issue because i took it apart to change the wifi card and noticed that the keyboard track pad are one unit so must be single driver?  thanks a ton!

---

### Post by &amp;KyT$0P# on 2017-03-01
We need a lot more information to be able to help you.  Please install inxi if you don't already have it...
```
sudo apt-get install inxi
```
... then post here the output of running this command in Terminal -
```
inxi -! 31 -Fxxz
```

---

### Post by jeff666 on 2017-03-01
problem solved you must press fn key for them to work :lolflag:

---

### Post by lisati on 2017-03-01
> **jeff666 said:**
> problem solved you must press fn key for them to work :lolflag:

If so, please mark the thread "solved" using the "Thread tools" drop-down menu.

---

