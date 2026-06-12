---
title: "Admin Password Lost (still have root's)"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Pabx on 2007-09-24
Hello ive got a problem, i forgot my password!!! :confused::( i know what you are thinking, but I still have root's password, I am in the root's account, but when i try to acces System>Administration>users and groups, i cant, isnt root the most important user? how can i restore my password? plz help! 


:confused::confused::confused:

---

### Post by Dr Small on 2007-09-24
Boot up in Recovery Mode, from GNU GRUB, and then type
```
passwd username
```

You will be logged in as root, and then you will be able to change the password of the account that you wish.

Dr Small

---

### Post by Pabx on 2007-09-24
> **Dr Small said:**
> Boot up in Recovery Mode, from GNU GRUB, and then type
```
passwd username
```

You will be logged in as root, and then you will be able to change the password of the account that you wish.

Dr Small

Thank you , i try and worked fine :)

---

### Post by Dr Small on 2007-09-24
Please remember to mark your threads as "SOLVED".

---

