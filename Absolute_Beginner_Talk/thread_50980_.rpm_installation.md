---
title: ".rpm installation"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2005-07-22
Hey, i have got a driver for my modem, how do i go about installing it? its in .rpm format.

---

### Post by bored2k on 2005-07-22
[QUOTE=KrisDwyer]Hey, i have got a driver for my modem, how do i go about installing it? its in .rpm format.[/QUOTE]
 You could try using
alien -d file.rpm
Then
"sudo dpkg -i file.deb" the file that generates

---

### Post by codejunkie on 2005-07-22
[QUOTE=KrisDwyer]Hey, i have got a driver for my modem, how do i go about installing it? its in .rpm format.[/QUOTE]
```
sudo alien -i  nameofile.rpm
``` this should install the package

---

