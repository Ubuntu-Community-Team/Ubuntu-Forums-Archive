---
title: "Complete Newbie Question"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by johncraft on 2006-05-29
Hi Guys,

I am very new to the linux environment.

My question is how do I find out what version of Ubuntu I am running?

Also how to I know if I am running:
Ubuntu Breezy - 0.7-4
               or
Ubuntu Dapper - 0.7-8


Thanks,
John

---

### Post by cskeide on 2006-05-29
You can check which version of ubuntu you're running by opening a terminal (Applications -> Accessories -> Terminal), and typing the following command:```
cat /etc/issue
```
> Also how to I know if I am running:
Ubuntu Breezy - 0.7-4
or
Ubuntu Dapper - 0.7-8
These are not ubuntu version numbers. You must be refering to some specific package within your installation.
To check for version numbers of a specific package, try this command:```
dpkg -l <packagename>
```

---

### Post by xyz on 2006-05-29
or also in a Terminal:
> lsb_release -a

---

### Post by johncraft on 2006-05-29
Thanks guys,

---

