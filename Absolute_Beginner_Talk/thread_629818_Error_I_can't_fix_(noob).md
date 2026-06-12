---
title: "Error I can't fix (noob)"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Eforce on 2007-12-02
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

This annoying error I always see when trying to install something on the terminal and it limits me.

I just installed ubuntu yestarday and I pretty much have no idea what this is.

I need help please.

---

### Post by spiderbatdad on 2007-12-02
you've had a package error. Open a terminal and enter:

```
sudo dpkg --configure -a
```

---

### Post by Eforce on 2007-12-02
Whenever it asks me for my password and I try to enter it nothing happens.

---

### Post by spiderbatdad on 2007-12-02
that is most likely a good thing. linux often carries out commands "silently" unless you request verbose output.

---

### Post by Eforce on 2007-12-02
Thank you a lot
Fixed it

---

