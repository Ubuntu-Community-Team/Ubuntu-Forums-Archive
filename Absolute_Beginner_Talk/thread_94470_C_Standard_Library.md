---
title: "C Standard Library"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2005-11-24
Hi,
How can I know that I have got C Standard Library on my Ubuntu?
How can I install it on my Linux?
Thanks,

---

### Post by Gustav on 2005-11-24
You probably have the library installed since almost all programs depend on it but you can check the package libc6 with synaptics or apt (but you need libc6 to run those programs :)).

But if you mean the development version (wich is good to have if you're programming C), do this in the terminal
```
sudo apt-get install libc6-dev
```

---

