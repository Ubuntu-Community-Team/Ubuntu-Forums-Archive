---
title: "Wine Compiling Problem"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by etorres on 2005-12-12
I got to the ./configure part of compiling wine 20040716.
It says        no acceptable C Compiler  found in $PATH

I don't know what this means or what I can do about it. Thanks

---

### Post by lreyes6 on 2005-12-12
that's because Ubuntu doesn't bring by default the compiling tools... so you need to install it... you can do it by synaptic just search for the build-essential package or do it in a terminal 

```
sudo aptitude install build-essential
```

hope this helps

---

