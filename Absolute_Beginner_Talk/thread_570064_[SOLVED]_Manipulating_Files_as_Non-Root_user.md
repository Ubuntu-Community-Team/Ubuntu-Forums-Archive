---
title: "[SOLVED] Manipulating Files as Non-Root user"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by effinboy on 2007-10-07
Example:
I have xampp installled and running on a headless machine with 7.04 desktop.
I have a vista laptop that I have network drives mapped out on.
I want to be able to manipulate the files in a root access folder by accessing them through vista while they are mapped on my local network.


Is there a setting to, perhaps, "unlock" a directory to allow my default user access to manipulate these files?

Thank you in advance. :D

---

### Post by Dr Small on 2007-10-07
```
man chmod
```

---

### Post by effinboy on 2007-10-07
Perfect.

If I understand everything correctly then

```
sudo chmod a+wrx dirname
```

should work just fine right?

Edit: That worked perfectly. Thank you again.

---

