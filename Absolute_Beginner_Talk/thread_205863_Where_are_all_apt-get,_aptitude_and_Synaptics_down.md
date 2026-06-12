---
title: "Where are all apt-get, aptitude and Synaptics downloaded archives stored?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-29
Hi,


Every time you install or upgrade your packages using either *apt-get*, *aptitude* or Synaptics, archives are being downloaded. Where do these archives go, I mean in which directory can I find them?

I'm a bit low on space on the linux partition and I can't resize it just now. This is why I need to clean up some space. I thought that getting rid of all these archives would help a little.

Thanks

---

### Post by addict3d on 2006-06-29
apt's packages are stored in /var/cache/apt/archives afaik..

---

### Post by aysiu on 2006-06-29
/var/cache/apt/archives

To clean it out: ```
sudo apt-get clean
```

---

