---
title: "How do I edit the xorg.conf file"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by RyanFaith88 on 2007-05-04
I need to edit the xorg.conf file.  Any help would be great.

---

### Post by aysiu on 2007-05-04
This will help you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by bodhi.zazen on 2007-05-04
Permissions are important to understand. 

You need root access to modify system files.

Open a terminal and enter the following commands (the first is to make a backup):

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```

_Note_: The default behavior of gedit is to make backups under name_of_file~ (adding a ~ to the end). I like to turn this off.

---

### Post by medya on 2007-05-04
the question is where do you want to edit it ? in graphical mode or text mode (command prompt) ?

for graphical mode use the above post , for text mode use nano

> sudo nano /etc/X11/xorg.conf

---

