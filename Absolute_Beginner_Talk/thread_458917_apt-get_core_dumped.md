---
title: "apt-get core dumped"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2007-05-30
i just did a fresh install.
i install aMSN 1st instead of updating the system.
and then, i want to install font
this is what i get:
```
sudo apt-get install msttcorefonts
Reading package list... Done
Segmention fault (core dumped(
```

---

### Post by apjone on 2007-05-30
try a apt-get update . then try. if not post output here

---

### Post by oliviacond on 2007-05-30
tried apt-get update.
output still the same for apt-get install
no problem for apt-get update

---

### Post by carloslosgrande on 2007-05-30
Hi, check this thread for a similar - resolved - problem
[http://ubuntuforums.org/showthread.php?t=454759&highlight=segmentation](http://ubuntuforums.org/showthread.php?t=454759&highlight=segmentation)

---

### Post by oliviacond on 2007-05-30
this command solved it
```

sudo rm -f /var/cache/apt/*.bin
sudo apt-get update

```

thanks ya

---

