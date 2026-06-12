---
title: "Amarok Help!"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by dillbertdabomb on 2006-12-21
I want to install amarok, but it says it needs amarok-xine, but when i try to install that, it tells me to install amarok. What am I doing wrong? I tried force installing it, but that makes the install system go mad...

---

### Post by PriceChild on 2006-12-21
Are you trying to do this with debs already downloaded by any chance?

If so then put them both in the same command, e.g.```
sudo dpkg -i <<amarok>> <<amarok-xine>>
```
However you're reccomended to use apt:```
sudo apt-get install amarok
```

---

### Post by dillbertdabomb on 2006-12-21
no internet on my ubuntu computer, but I will try that.

---

