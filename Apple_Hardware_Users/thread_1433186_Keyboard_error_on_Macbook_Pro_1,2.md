---
title: "Keyboard error on Macbook Pro 1,2"
date: 2010-03-18
forum: Apple Hardware Users
---

### Post by BinaryDigit on 2010-03-18
Hi All,
Has anyone seen this keyboard error before? I tried to set it up in System, Preferences, Keyboard and select Apple -> Macbook/Macbook Pro.  (I have an US keyboard Macbook Pro 1,2)

Perhaps it's a bug like it says?

---

### Post by phildini on 2010-03-21
Have you tried running the suggested commands? Additionally, you may want to try reposting this question in one of the categories more likely to deal with xorg issues, like Desktop Environments or Hadware & Laptops.

---

### Post by kmag on 2010-03-21
I had the exact same thing.  Try removing mouseemu.  You can do it from Synaptic if your keyboard works but  I had to do it from the command line since my keyboard would not work in Gnome, therefore no password entry possible.

command from terminal is:
sudo apt-get --purge remove mouseemu

---

### Post by linuxopjemac on 2010-03-21
if you want to remove mouseemu from the terminal:
```
sudo apt-get remove mouseemu
```

---

