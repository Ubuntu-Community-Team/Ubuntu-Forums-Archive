---
title: "restore admin privileges"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by plico on 2007-08-20
it looks like I removed from my first user the admin privileges. how can I restore them?
right now I can't see anymore the user manager icon nor the add application.:(:(
I can still di sudo since I know the root password but I don't know how to restore my admin privileges.

thank you very much for your help

---

### Post by Dr Small on 2007-08-20
did you try:
```
gksudo users-admin
```

?

---

### Post by schorsch on 2007-08-20
If you still know the root password:
```
su -
usermod -aG admin *username*
```

---

### Post by plico on 2007-08-20
ok, it worked.

thank you very much:)

---

### Post by schorsch on 2007-08-21
o.k. could  you please mark the thread as solved as this may help others, too?

---

