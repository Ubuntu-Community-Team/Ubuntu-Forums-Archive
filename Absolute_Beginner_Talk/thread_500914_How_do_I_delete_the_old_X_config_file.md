---
title: "How do I delete the old X config file"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Meogeo on 2007-07-14
I have made a mess of my X config file. How do I delete it and rename the backup. I am in the Black screen.

Many thanks

---

### Post by meierfra on 2007-07-14
In the terminal type:

cd  /etc/X11/       

sudo rm xorg.conf

sudo  cp nameofbackupfile  xorg.conf


To find out the name of the backup file   type 

ls

This will list all file in the folder /etc/X11

---

### Post by Meogeo on 2007-07-14
Thats done the trick.

Thanks

---

