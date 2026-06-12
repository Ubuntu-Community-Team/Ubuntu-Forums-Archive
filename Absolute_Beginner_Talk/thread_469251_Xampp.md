---
title: "Xampp"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by trueblue64 on 2007-06-09
I have run xampp ok in windows now opted for Ubuntu, I need to copy a folder into htdocs folder It says I dont have permissions. please help

---

### Post by ferpadro on 2007-06-09
I had the same problem. U need to create a symbolic link into your home directory that points to htdocs. This way whatever document you save into the folder you created the symbolic link into will also be created in /opt/xampp/htdocs, at least thats the way it worked for me.

Regards

---

