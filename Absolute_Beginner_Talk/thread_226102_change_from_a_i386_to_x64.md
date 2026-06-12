---
title: "change from a i386 to x64"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Bdubbya on 2006-07-30
The pc I'm useing now is a x64 AMD.

I used the i386 just to get it working at all.

If there a way to load the x64 kernel into my current installation or do i need to start from scratch?

---

### Post by Jagot on 2006-07-30
You should just be able to do this:

```
sudo aptitude update
sudo aptitude install linux-image-amd64-generic
```

---

