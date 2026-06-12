---
title: "X is missing!"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-05-21
I have encountered this a few times already:
```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

In other cases that I have encountered, X libraries are missing.

What could be wrong?

---

### Post by taurus on 2007-05-21
Are you trying to compile something from source?

---

### Post by RedSquirrel on 2007-05-21
> **wersdaluv said:**
> I have encountered this a few times already:
```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```In other cases that I have encountered, X libraries are missing.

What could be wrong?

You need to install the development libraries:

```
sudo apt-get update
sudo apt-get install xorg-dev

```

---

### Post by daxumaming on 2007-06-03
also experiencing the same error, installing xlibs-dev fixed it.

---

### Post by wersdaluv on 2007-06-03
> **daxumaming said:**
> also experiencing the same error, installing xlibs-dev fixed it.

Wow! Cool, pare! Pinoy pa! hahaha :)

---

