---
title: "Broken dependencies"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by rajaram_s on 2008-03-27
I have ubuntu 7.10. I recently installed a few debina packages, for one of which the package manager said, all dependencies satisfied and the install button was enabled. In between the installation, it said the package has broken dependencies. I tried 

sudo synaptic

and tried to remove the broken packages using the package filter. To my surprise it shows that almost all packages are to be removed to solve the broken dependency issue. I dont have direct internet connection too on my computer. So its very difficult for me to get the packages back. What do I do?

---

### Post by adityakavoor on 2008-03-27
```
sudo apt-get install -f
```

---

### Post by mrsudo on 2008-03-27
i had the same problem
worked for me :)

---

### Post by dstew on 2008-03-27
If you don't have an internet connection, try the [nonetdebs]("http://nonetdebs.homeip.net/") web site. You can install with dependencies, and update using their service.

---

### Post by rajaram_s on 2008-03-27
Thank you so much for the link.Since I dont have d comp rt now, I'll I will try the apt-get install -f and get back with the results soon

---

### Post by adityakavoor on 2008-03-27
also try getgeb.net

---

### Post by forrestcupp on 2008-03-27
> **dstew said:**
> If you don't have an internet connection, try the [nonetdebs]("http://nonetdebs.homeip.net/") web site. You can install with dependencies, and update using their service.

Awesome find.

After you do the command above, also do
```
sudo apt-get update
```

---

