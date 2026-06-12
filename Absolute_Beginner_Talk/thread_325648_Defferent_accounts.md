---
title: "Defferent accounts"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by tenwesta on 2006-12-26
](*,) I somehow mannaged to change my admin account (changed user name and password), but now problem is that a couldn't run the login with that account because it tells me that my account doesnt have home directory.

---

### Post by tzulberti on 2006-12-26
Maybe you used: adduser, but you should used useradd, becuase this last one creates the home folder,and some configuration files.
My advice: delete the user, using deluser, and then create it again using useradd

---

### Post by tenwesta on 2006-12-26
> **tzulberti said:**
> Maybe you used: adduser, but you should used useradd, becuase this last one creates the home folder,and some configuration files.
My advice: delete the user, using deluser, and then create it again using useradd


I already made another account. But then when I login i couldnt run any system administration stuff because it tells me that im not allowed to access the system configuration.

---

