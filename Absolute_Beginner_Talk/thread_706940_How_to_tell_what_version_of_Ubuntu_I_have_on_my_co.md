---
title: "How to tell what version of Ubuntu I have on my computer?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by JEBB on 2008-02-24
How can I tell what version of Ubuntu I have on my computer?  None of the menu choices seem to take me to that information.  Thanks.

---

### Post by spiderbatdad on 2008-02-24
System>>Administration>>System Monitor...system tab.

---

### Post by tango_ninja on 2008-02-24
I believe you can access it via the menu..

System > About Ubuntu

and it will open a window telling you which version is installed (Gutsy 7.1 does this anyway, just checked)

---

### Post by Presto123 on 2008-02-24
Hey there. It's located in System/Administration/System Monitor in the "System" tab.

---

### Post by LaRoza on 2008-02-24
In the terminal:

```

less /etc/issue

```

---

### Post by Buffalo Soldier on 2008-02-24
enter these commands in the terminal (Applications -> Terminal):
```
uname -a
```
```
lsb_release -a
```

---

### Post by Lysander10 on 2008-02-24
Go to System > About Ubuntu. It will tell you on that screen what version you are running.

---

### Post by Presto123 on 2008-02-24
LOL...lots of different ways. :)

FYI: none of these are wrong ways of finding out.

---

### Post by JEBB on 2008-02-25
Thanks for the replies.  

System>About Ubuntu gives a textual response that looks more like an ad.  The command lsb_release -a gave the best response.

---

### Post by incen on 2008-02-25
It's really cool to know there are many ways to approach though. Nice! :mrgreen:

---

