---
title: "Update changed boot load"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by eiolv on 2007-05-30
What happened? I run an automatic Ubuntu update and it changed grub, ommitting the choise to boot Windows and dubling the Ubuntu choises. I changed it back, but why can something like that happen?

---

### Post by plcdfa on 2007-05-30
Everytime it installs a new kernel version the grub menu file is also updated. It should automatically include any windows partitions, but it can't do it in every case.Seems like you'll have to add it back by hand every time. (Or possibly you could play a bit with the default options in menu.lst to solve this, I'll take a look at it when I get home.)

---

