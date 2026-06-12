---
title: "Desktop Icon"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by danbrownlow on 2007-04-12
Hey, I downloaded an RPM file and was goin' to install it, but now for some reason, theres a padlock sign beside it and I can't delete it because I don't have the permissions.. I don't want it there so does anyone know how I can delete it?
Thanks

---

### Post by Obor on 2007-04-12
Maybe someone else will tell you why you don't have permissions but to delete it open terminal and:
```
cd Desktop
sudo rm nameofthefile
```
Thats if it is on the desktop. Otherwise cd /path/to/folder/
just start typing the name of the file and press TAB it will type the rest of the file name for you

---

### Post by danbrownlow on 2007-04-14
Hey, I tried this already but it says cannot remove as it's a directory or something :S

---

### Post by Compyx on 2007-04-14
```
cd ~/Desktop
sudo rm -rfd <name-of-file-or-directory>
```

---

