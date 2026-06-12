---
title: "su password cracker"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2007-01-22
ok, so i have a stupid newbie problem, i have totally forgotten my su password, does anyone know of any cracker programs available

---

### Post by ardchoille42 on 2007-01-22
> **Sniper99 said:**
> ok, so i have a stupid newbie problem, i have totally forgotten my su password, does anyone know of any cracker programs available

You can just boot into recovery mode and change your admin pasword. I believe the passwords are held in a hashed state in /etc/shadow. I believe MD5 or SHA1 is used to hash passwords, so, I don't think a password cracker would work. But, I may be wrong.

---

### Post by aysiu on 2007-01-22
You shouldn't have an *su* password, since Ubuntu users *sudo* instead of root.

But if you want to reset the password for your *sudo* (or admin) user, reboot into recovery mode and type ```
passwd *username*
reboot
```

---

### Post by CroEragon on 2007-01-22
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

I googled it, i didnt know how to do it just like you when i opened thread.
Google is your friend.

---

