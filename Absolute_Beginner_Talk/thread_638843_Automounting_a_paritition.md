---
title: "Automounting a paritition"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-12-12
I am currently dual booting between windows xp and ubuntu gutsy. When I am in Gutsy, if I want to access the windows partition, I have to click on the "unmounted" icon for the windows partition and put in my password. How can I change it so that it can be automatically mounted without the need for the password?

---

### Post by meborc on 2007-12-12
there should be a ntfs configuration utility in one of the menus (probably the admin)

if not, install it:
```
sudo apt-get install ntfs-config
```
then launch it from the menu

---

### Post by noorez on 2007-12-12
This utility only had an option for enabling writing to external drives. The write to internal drives was grayed out. I want to be able to mount the partition automatically on startup and without needing my password.

---

### Post by thelatinist on 2007-12-12
[http://ubuntuforums.org/showthread.php?p=3915803#post3915803](http://ubuntuforums.org/showthread.php?p=3915803#post3915803)

---

