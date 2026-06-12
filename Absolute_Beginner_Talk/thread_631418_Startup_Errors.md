---
title: "Startup Errors ?"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-12-04
Yeah, now everytime I boot Ubuntu , I get a forced check on sda1 and sda3
with it saying that they "contain a file system with errors" "check forced".
How can I see what the errors are,and fix them ? It goes through the check,
then it says "OK" and boots fine,  :confused:

---

### Post by Dr Small on 2007-12-04
> **Drakkor said:**
> Yeah, now everytime I boot Ubuntu , I get a forced check on sda1 and sda3
with it saying that they "contain a file system with errors" "check forced".
How can I see what the errors are,and fix them ? It goes through the check,
then it says "OK" and boots fine,  :confused:
I have had it where I couldn't boot before because of errors, and had to run this command:
```
fsck /dev/sda3
```

---

### Post by Drakkor on 2007-12-04
I get this:
drakkor@Godzilla-Leon:~$ fsck /dev/sda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
drakkor@Godzilla-Leon:~$

---

### Post by ajgreeny on 2007-12-04
You can't fsck a mounted drive so try it using the live CD, making sure drives are unmounted first.

---

### Post by Driv3r912 on 2007-12-04
> **ajgreeny said:**
> You can't fsck a mounted drive so try it using the live CD, making sure drives are unmounted first.

yup, that should do it.

---

