---
title: "compiz not working"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-03-29
compiz doesn't work on my PC which has got an intel graphics controller,1 gb RAM and a core2duo intel processor with a clock speed of 2 GHz.it seems like my driver is blacklisted.will the installation of appropriate drivers solve the issue,how can i know as to which driver would work in my case,how do i install them,i am absolutely new to linux,and have always ben nothing more than an average computer user.so please help,and give me a detailed solution.i can't run desktop effects even after configuring compiz.how can i get them running.

---

### Post by Ub1476 on 2008-03-29
To see what intel controller you use, write this onto the terminal:

```
lspci | grep VGA
```

[Here's]("Here's") the sticky describing the blacklist problem.

---

