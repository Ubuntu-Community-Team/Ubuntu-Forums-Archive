---
title: "format flash memory"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2007-06-25
how do you format flash memory in fiesty fawn

---

### Post by skymera on 2007-06-25
what do u mean 'flash' memory>?

a data stick?

---

### Post by BlackMeTaL on 2007-06-25
You can try to find you flash memory device with the command dmesg. Mine is /dev/sda1
You can then format it from the terminal: mkfs.vfat /dev/sda1

If you want to do it graphically you can also use the program gparted

---

