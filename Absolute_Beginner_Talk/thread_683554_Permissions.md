---
title: "Permissions"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by oberengu on 2008-01-31
Hello All!
I try to change the content of a file and I cannot.
The computer says: "You don't have the permissions necessary to save the file...".
Please help me.
Thanks for advance...

---

### Post by p_quarles on 2008-01-31
Which file, and how are you trying to open it?

---

### Post by oberengu on 2008-01-31
C/etc/modules
I am trying to add some instructions with a text editor (gedit).

---

### Post by jflarm on 2008-01-31
sudo gedit /etc/modules
Then you put your password....that should do it.

---

### Post by p_quarles on 2008-01-31
Open a terminal and type the following:
```
gksudo gedit /etc/modules
```
You will be prompted for your password, and then will be able to edit the file.

Please be very careful when editing that file, though. Doing something wrong there can break your installation.

---

