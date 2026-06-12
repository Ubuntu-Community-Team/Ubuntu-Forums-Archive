---
title: "dvd repositories"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by stunningman on 2008-01-26
I have a dvd which contains ubuntu repositories.earlier it was easy to install any repositories from this dvd on ubuntu.but now i cannot install any package from it.whenever i try it says not accessible. i thought that the packages might have got corrupted.so i try to copy all the contents in winxp and it works fine and got copied without any error of corrupted file.
is there any way to write these file packages on a blank dvd and use that dvd in ubuntu.
looking for your advice.

---

### Post by Paul820 on 2008-01-26
Use K3b or gnomebaker and copy it.

---

### Post by Christmas on 2008-01-26
Try
```
sudo apt-cdrom add
```
Then insert your DVD and wait to scan it. Now update your repos:
```
sudo apt-get update
```

---

