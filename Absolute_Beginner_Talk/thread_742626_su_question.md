---
title: "su question"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by twist2b on 2008-04-01
I I have feisty (7.04)
When I type "su" in the terminal it requests password AND I type MY password it does NOT work....... WHY?

Ive tried alot of others like root, admin, pass, passwrd, password.

Thanks for suggestions.

---

### Post by jrharvey on 2008-04-01
try sudo

---

### Post by jken146 on 2008-04-01
You need ```
sudo su
``` or ```
sudo -i
```

su on its own would need the root password, which is not set.

---

### Post by Duck2006 on 2008-04-01
Try sudo su

---

### Post by twist2b on 2008-04-01
Thank you guys, Sudo su worked perfect! I should have known! THank you!!!!!

heres some popcorn! :popcorn:

---

### Post by N1N31NCHN41L5 on 2008-04-01
Don't forget to mark the thread as solved if you have all the answers you were looking for initially on this post.

---

