---
title: "How to get rid of failed driver installation"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by bryan4134 on 2006-09-07
The installation of a modem driver failed a few days ago.  Now everytime I apply new unrelated updates this driver keeps trying to install itself (and fails) - this causes the updates that I do want to get hung up until I manually open the console window and kill the offending driver.  How can I delete this offending driver - I can't seem to find where it is located.

Using 6.06

Thanks

---

### Post by taurus on 2006-09-07
If you know the name of the package/driver, you can use aptitude to remove it...

```
sudo aptitude remove <package_name>
```

---

