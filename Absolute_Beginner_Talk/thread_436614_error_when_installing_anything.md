---
title: "error when installing anything"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by simplekin on 2007-05-08
ok, i get this message after trying to install my ati drivers, or something else:

Errors were encountered while processing:
 amavisd-new
 amavisd-new-milter

was wondering how i can fix this

---

### Post by ctsdownloads on 2007-05-08
Hi, would love to help.

Walk me through the process as completely as you can so we can get this figured out. :)

---

### Post by jfinkels on 2007-05-08
I assume you tried to install amavisd at some point...What happens when you type the following command:
```

sudo aptitude remove amavisd-new amavisd-new-milter

```
Or maybe you can try installing it, then removing it:
```

sudo aptitude install amavisd-new amavisd-new-milter && sudo aptitude remove amavisd-new amavisd-new-milter

```

---

### Post by simplekin on 2007-05-08
> **jfinkels said:**
> I assume you tried to install amavisd at some point...What happens when you type the following command:
```

sudo aptitude remove amavisd-new amavisd-new-milter

```
Or maybe you can try installing it, then removing it:
```

sudo aptitude install amavisd-new amavisd-new-milter && sudo aptitude remove amavisd-new amavisd-new-milter

```


thank you, that worked!

---

