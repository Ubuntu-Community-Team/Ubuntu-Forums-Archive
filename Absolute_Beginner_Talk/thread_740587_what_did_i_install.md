---
title: "what did i install?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by smallmouth sam on 2008-03-30
How do I tell if i am runnuing 64 bit ubuntu?

 can I run 32 it ubuntu with amd 64 chip?

how do I get it?

---

### Post by jordanmthomas on 2008-03-30
Yes, you can run 32-bit with an AMD 64-bit.

To tell which kernel you're using, post back the output of
```
uname -r
```
If it says 2.6.xx-generic, you're using the 32-bit kernel.

---

### Post by akiratheoni on 2008-03-30
Yes, you can a 32 bit ubuntu with an AMD64 chip. It's just that the 64 bit version is more optimized for your processor so you'll take a small hit in performance.

To find out if you are running 64 or 32 bit Ubuntu, open the terminal (Applications -> Accessories -> Terminal) and type in:

> uname -a

If the output says 'i686 GNU/Linux' then that's 32 bit. I'm not sure what it would say if it is 64 bit but probably AMD64.

---

### Post by Inxsible on 2008-03-30
For a 64 bit OS it would say this
```
Linux HPdv9000t 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
```Note the x86_64. And like akira said, for 32 bit it would be i686

---

### Post by jordanmthomas on 2008-03-30
> **Inxsible said:**
> For a 64 bit OS it would say this
```
Linux HPdv9000t 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
```Note the x86_64. And like akira said, for 32 bit it would be i686

Ooh, in that case disregard my post.  I didn't realize it would still throw the generic on the end of the kernel name.  I figured it'd put -amd64 or something similar.

My apologies to the op.

---

