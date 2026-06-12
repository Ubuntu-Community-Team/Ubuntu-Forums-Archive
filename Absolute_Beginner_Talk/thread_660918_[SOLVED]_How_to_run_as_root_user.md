---
title: "[SOLVED] How to run as root user?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by hnprashanth on 2008-01-07
It's been a week am started using Ubuntu, everything worked fine until now. But now if i run any command like** dpkg-reconfigure xserver-xorg** it says "/usr/sbin/dpkg-reconfigure must be run as root"

I don't Understand what does that mean. I am the only user for this ubuntu installation. How to run as root?

---

### Post by bellzii on 2008-01-07
type 

sudo su

---

### Post by perlluver on 2008-01-07
Always type sudo before anything else that you want to run as root.  This will allow you to become root temoprarily.  Example ```
sudo apt-get update
```

---

### Post by hnprashanth on 2008-01-07
Thanks a lot....:KS

---

