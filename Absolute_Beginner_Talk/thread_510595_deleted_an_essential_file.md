---
title: "deleted an essential file"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by maldojr88 on 2007-07-26
hey i need help here
i was configuring the smb.conf file 
locate on /etc/samba

and i accidentally deleted the content of the file 

is there a way to get back the file...or wat can i do?????

---

### Post by jaffamuffin on 2007-07-26
Write it again ? ? 

google for smb.conf examples

Read the Samba how to.

man smb.conf

[http://www.comptechdoc.org/os/linux/manual4/smbconf.html](http://www.comptechdoc.org/os/linux/manual4/smbconf.html)  for a detailed example.

---

### Post by raja on 2007-07-26
Deleted the content of the file? - Then you can just close it without saving.
If you meant you deleted the file, look for it in ~/.Trash.

---

### Post by misfitpierce on 2007-07-26
Maybe hit the Synatpic package manager and erase everything samba then reinstall?

---

### Post by maldojr88 on 2007-07-26
how do i uninstall and then install it back again????

---

### Post by nickburns on 2007-07-26
sudo apt-get --purge remove samba  

will uninstall

sudo apt-get install samba

will bring it back.

---

### Post by nickburns on 2007-07-26
Here is a blank config file...

Just need to rename it without the .txt

---

