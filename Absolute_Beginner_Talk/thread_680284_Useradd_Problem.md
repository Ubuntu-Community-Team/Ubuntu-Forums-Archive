---
title: "Useradd Problem"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by durdensbuddy on 2008-01-27
When I attempted to add a user I got the following error:

shannon@shannon-desktop:~$ useradd sgroves
useradd: unable to lock password file
shannon@shannon-desktop:~$

What's happening here?  

Ubuntu 7.10 AMD64

---

### Post by Kilz on 2008-01-27
try 
sudo useradd sgroves

---

### Post by Majorix on 2008-01-27
Try putting a sudo in front.
Like this:
```
sudo useradd -s -m sgroves
```

---

### Post by durdensbuddy on 2008-01-27
what are the -s and -m commands?

---

### Post by Majorix on 2008-01-27
You can read about them and more in
```
man useradd
```

---

