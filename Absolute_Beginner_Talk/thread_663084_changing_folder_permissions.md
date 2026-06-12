---
title: "changing folder permissions"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by kizmet_x on 2008-01-09
I just installed Unreal Tournament 2004. As part of the install, I wrote it to /home/my user name/games/ to create a custom folder to install games into, while being able to patch them without using sudo. I figured this way would be easier. However, when I created the games folder, its marked root-only. How can I change the permission to where I can write on it? Thanks in advance.

---

### Post by taurus on 2008-01-09
You can change the ownership of that new directory back to your login name so you can write to it anytime you want.

```
sudo chown -R **username**:**username** ~/games
```

---

### Post by beercz on 2008-01-09
Does this help?

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by NovaAesa on 2008-01-09
GUI method:

Right click on the folder and go to Permissions. Change the group to your username and hit close. If there are files in the folder, you might want to click Apply Permissions To Enclosed Files.

---

