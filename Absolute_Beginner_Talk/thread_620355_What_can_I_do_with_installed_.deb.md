---
title: "What can I do with installed .deb?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by djseeker2007 on 2007-11-22
After installing some packages and upgradings, I found in /var/cache/apt/archives all the installed .deb files, and they take up a lot of space in my hard drive. I wonder whether it is safe if I delete them? Thanks in advance.

---

### Post by aysiu on 2007-11-22
It's safe. The command to delete them is ```
sudo apt-get clean
```

---

