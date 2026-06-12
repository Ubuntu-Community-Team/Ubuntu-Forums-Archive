---
title: "I crashed my system :D"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by Enter on 2006-03-26
anyway i was bored so i tryed instaling AC97 ALC850 driver runing it without sudo didnt work very well so i gave it sudo, now i think it deleted libasound.so.2 because when i try to log in it gives me error that it cant find this lib and it logs me out :D
Now how do i fix that, reinstall ubuntu?

---

### Post by Aewheros on 2006-03-26
Try to just reinstall libasound.so.2 in text mode. Press CTRL+ALT+F1 instead of logging into gnome, write your username at the login prompt and when you are logged in type:
```
sudo apt-get install libasound.so.2
```

Press CTRL+ALT+F7 to return to graphical mode.

---

### Post by Enter on 2006-03-26
it didnt work

---

### Post by dermotti on 2006-03-26
[B]sudo apt-get remove libasound2

sudo apt-get install libasound2[/B]

---

### Post by Enter on 2006-03-26
sudo apt-get remove libasound2
removed all programs with GUI xD
now im left with terminal great, anyone know how to fix that

---

### Post by Enter on 2006-03-26
cna someone explain how do i reinstall ubuntu without deleting my files?

---

### Post by oscar on 2006-03-26
```
sudo apt-get install ubuntu-desktop
```

should get you back up with the basics

---

