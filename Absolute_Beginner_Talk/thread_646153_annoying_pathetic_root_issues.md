---
title: "annoying pathetic root issues"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by chips24 on 2007-12-20
i cant open my usr/share/icons/human because i dont have permission. so i tried to login as root but it says its the incorrect user name and password, iv also tried "su -l" but it says authentication error after i type  my pass, but... i  can type sudo -l ... but asks for my username password, and not my root password, so i still cant access the folder. need help.](*,)

---

### Post by PmDematagoda on 2007-12-20
Give:-

```
gksudo nautilus
```
a try. That will open Nautilus in Root mode.

---

### Post by finferflu on 2007-12-20
Root account is disabled by default on Ubuntu. Have you tried with

```
sudo su
```
?

Also you don't really need to login into the session as root, just run nautilus as root, if you need to:

```
sudo nautilus
```

---

### Post by MrFSL on 2007-12-20
Or you can change ownership / permissions on the directory.

You can display the current settings using:
```
ls -ldp /usr/share/icons/human
```

```

sudo chown username /usr/share/icons/human
chmod 755 /usr/share/icons/human
```

---

