---
title: "Xorg configuring?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by NyTE on 2006-04-30
Whats the command so I can edit my xorg config?:-k

---

### Post by chinook on 2006-04-30
sudo dpkg-reconfigure xserver-xorg

---

### Post by bluevoodoo1 on 2006-04-30
sudo gedit /etc/X11/xorg.conf

back it up first

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

---

### Post by tseliot on 2006-04-30
You can edit it as a text:
```
sudo nano /etc/X11/xorg.conf
```


or

just answer some questions:
```
sudo dpkg-reconfigure xserver-xorg
```

EDIT: Aarrg, someone was faster than me to answer ;-)

---

### Post by NyTE on 2006-04-30
Thanks alot guys.Edited what needed to be edited.

---

