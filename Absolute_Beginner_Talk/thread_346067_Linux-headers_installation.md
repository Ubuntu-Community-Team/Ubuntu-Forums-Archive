---
title: "Linux-headers installation"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by lukic on 2007-01-25
How ca I install linux-headers from Ubuntu CD? I am using Ubuntu 6.06.

I tryed: 

```
sudo apt-cdrom add
```

```
sudo apt-get install linux-headers-xxxxxx
```

But it is not working.Apt-get trys to download them form the internet and I don't want that if I don't have to.

Can someone help please?

---

### Post by RomeReactor on 2007-01-25
Hi. Maybe this will help: Open Synaptic and go to "Settings-->Repositories" and uncheck everything in the first three tabs, then add your cdrom in that third tab; then click reload and see if it works.

---

### Post by lukic on 2007-01-25
It helped! Thanks a lot!

---

