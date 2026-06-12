---
title: "Executing a precompiled binary?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-02-22
How do I execute a precompiled binary?  I did chmod +x links-0.99 and then tried running it with ./links-0.99 but it says "bash: ./links-0.99: No such file or directory".

Thanks.

---

### Post by taurus on 2008-02-22
Are you sure you have links-0.99 for the right arch?

Can you post the outputs of these commands, in the same directory where links-0.99 is resided?

```
uname -a
file links-0.99
ldd links-0.99
```

---

### Post by Yes on 2008-02-22
Nevermind, I guess I needed the linux-glibc2 binary.  How do I know what one I need (the first one I tried was linux-libc5)?

---

