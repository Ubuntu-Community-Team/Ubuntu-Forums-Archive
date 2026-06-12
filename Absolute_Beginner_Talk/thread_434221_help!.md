---
title: "help!"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by rick21saxo on 2007-05-05
i need help with " barebones" installation. (  sudo dpkg-reconfigure xserver-xorg  ) is not working, says it is not installed

---

### Post by taurus on 2007-05-05
Did you install a server version and now you want a desktop?

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

