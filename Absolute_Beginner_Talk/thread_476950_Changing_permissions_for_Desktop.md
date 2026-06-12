---
title: "Changing permissions for Desktop"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-06-17
For some reason, I can't seem to do anything to my desktop:  I can't delete anything from it, and I can't make new files/folders in it.  So, how can I change the permissions for it so I can do all that?

Thanks.

---

### Post by tanelt on 2007-06-17
Right-click on the "Desktop" folder in your Home folder and check the permissions for it.

---

### Post by Clay_Banger on 2007-06-17
```
cd ~/
ls -l
```
scroll through the list till you get to the entry for the folder "Desktop" and copy and paste that line here.

---

### Post by Yes on 2007-06-17
It says the owner is root.  How do I change that?

Thanks.

Edit: Here:

```
drwxr-xr-x 3 root root    4096 2007-06-17 17:30 Desktop
```

---

### Post by Clay_Banger on 2007-06-17
```
sudo chown -R username ~/Desktop
```
typing that into the terminal should to the trick, replacing "username" with your username

---

