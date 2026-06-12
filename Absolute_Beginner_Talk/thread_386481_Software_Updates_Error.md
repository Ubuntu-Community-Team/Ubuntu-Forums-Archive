---
title: "Software Updates Error"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by harerama on 2007-03-17
Hi,

Software Updates notification message appeared as usual. But when I tried to install the Updates. Error message appears and I can not update softwares.

The Error message says this 

> An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Since I have no idea what to do. I seek your help.

Thanks in advance.

---

### Post by Kateikyoushi on 2007-03-17
Copy the following line to the terminal, Applications > System tools > terminal.

```
sudo dpkg --configure -a
```

---

### Post by harerama on 2007-03-17
Cheers, Kateikyousi

It worked well,

Thanks for your help.

---

