---
title: "C sheel or Bourne shell"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-14
How does one make sure that one has C shell or Bourne shell .

---

### Post by taurus on 2006-12-14
```
finger
```

---

### Post by lance_klusener on 2006-12-14
finger is giving me only login information. Can i conclude something with this info. about the c shell or bourne shell

---

### Post by taurus on 2006-12-14
```
finger -l
```

---

### Post by smyru on 2006-12-14
env | grep SHELL

---

### Post by lance_klusener on 2006-12-14
so the shell says that it is /bin/bash. I assume it means this is bourne shell

---

### Post by Loco_gr on 2006-12-14
```
echo $SHELL
```

---

### Post by taurus on 2006-12-14
Yip.  And if you want to use /bin/csh from now on, then you can change it with

```
chsh
```
Then, log out and back in again you will be in /bin/csh environment...

---

### Post by Loco_gr on 2006-12-14
> **lance_klusener said:**
> so the shell says that it is /bin/bash. I assume it means this is bourne shell

Yes!!!

**B**ourne **A**gain **SH**ell

---

### Post by lance_klusener on 2006-12-14
Thanks everyone for your help .

---

