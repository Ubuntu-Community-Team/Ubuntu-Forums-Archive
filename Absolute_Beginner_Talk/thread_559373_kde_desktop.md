---
title: "kde desktop"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by SomeBuntu on 2007-09-25
I have just installed the kde desktop on my Ubuntu system. Now I get the blue Kubuntu startup screen on boot. How can I revert to my original Ubuntu screen ?

---

### Post by por100pre1 on 2007-09-25
If you mean the **login screen**, do this:

```
sudo dpkg-reconfigure gdm
```

and select gdm

```
sudo dpkg-reconfigure kdm
```

and select gdm

---

