---
title: "Ubuntu doesn't see my dual cpu?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2007-01-11
In the system monitor it only shows one CPU, I thought it was supposed to show two when a dual cpu is present, am I incorrect?

---

### Post by housam on 2007-01-11
You just have to install the smp kernel


 ```
sudo apt-get install linux-686-smp  
```

you can see both processors after restarting
 ```
cat /proc/cpuinfo
```

---

