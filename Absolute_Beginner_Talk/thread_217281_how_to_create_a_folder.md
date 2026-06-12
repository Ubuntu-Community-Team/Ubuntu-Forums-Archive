---
title: "how to create a folder"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-07-16
i installed apollon file sharing prog. it asks me to select a folder (GIFT)
AS /USR/SHARE/GIFT there is no such folder and when i try to create it it tells me i do not have permissions to do so. how do i get this permission and create the gift folder. thank you

---

### Post by Kilz on 2006-07-16
> **abu-fatu said:**
> i installed apollon file sharing prog. it asks me to select a folder (GIFT)
AS /USR/SHARE/GIFT there is no such folder and when i try to create it it tells me i do not have permissions to do so. how do i get this permission and create the gift folder. thank you
```
sudo mkdir /usr/share/GIFT

```
but you might want to make a folder in yout home folder and point it to that. Unless you want to change the owner of that folder to you. Otherwise it will be hard to add things to share. You will also have a hard time deleting things. Just change <username> to your username to change who owns that folder.
```
sudo chown -R <username>:users /usr/share/GIFT
```

---

### Post by aysiu on 2006-07-16
```
sudo mkdir /usr/share/gift
```

---

### Post by abu-fatu on 2006-07-16
thank you guys are the best. ubuntu has been such a great learning experience so far. i feel so much in control to be able to affect this system as needed.

---

### Post by catlett on 2006-07-16
Just to point out something you may already know and that other posters are alluding to. Linux is case sensitive. So /USR/SHARE/GIFT is not the same folder as /usr/share/gift and that is not the same folder as /usr/share/GIFT

---

