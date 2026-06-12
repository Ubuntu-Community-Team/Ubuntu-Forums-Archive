---
title: "FS in read only"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Ruen-Rybnik on 2008-03-26
The file system on my system disk is set to read only for all users.

i cant change this using the permisions properties tab i am assuming because it cant alter the text files.



any known solutions?

regards,


Ruen

---

### Post by Existentialist on 2008-03-27
Why do you need to write to any of the system files as a user?  If you need to edit a config file for example, you can use sudo to edit the files.  For example, you could edit xorg.conf by typing:

sudo nano /etc/X11/xorg.conf

I assume you can read and write to your home directory and files you create?

---

