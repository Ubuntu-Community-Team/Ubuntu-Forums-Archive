---
title: "owner?"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by firefly123 on 2006-01-11
I need to get permission to delete files from folders, Cant do need owners permission. Have tried groups and settings no go, so how do i log on as owner as i have not set password or anything:confused:

---

### Post by Thirsteh on 2006-01-11
You need to use the sudo command to do anything that requires super-user priveledges or priveledges that your normal user just doesn't have.

E.g.:
sudo rm /home/seconduser/Desktop/horse.avi

Would delete the horse movie from seconduser's Desktop.

The password for sudo is the same password as your main account's.

---

### Post by blackbeastofaarrgh on 2006-01-11
You can also use sudo chmod 777 [name of file] to give you permission to change the file. try man chmod for more info.

---

### Post by aysiu on 2006-01-11
[QUOTE=firefly123]I need to get permission to delete files from folders, Cant do need owners permission. Have tried groups and settings no go, so how do i log on as owner as i have not set password or anything:confused:[/QUOTE] Read the third link of my signature.

---

