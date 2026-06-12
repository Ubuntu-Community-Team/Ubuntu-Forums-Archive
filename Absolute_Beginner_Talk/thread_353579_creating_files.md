---
title: "creating files"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-02-04
I know this is a dumb question, but i need to create a file from the terminal called:

/etc/xinetd.d/swat


to add the contents:
--------------------------------------------
# description: SAMBA SWAT
service swat
{
    disable         = no
    socket_type     = stream
    protocol        = tcp
    user            = root  #should use a more limited user here
    wait            = no
    server          = /usr/sbin/swat
}
------------------------------------------------

---

### Post by Loki57701 on 2007-02-04
how do i do that?

---

### Post by k1001001 on 2007-02-04
Open gedit (sudo gedit in the terminal), copy and paste the contents, then go to "File" and "Save As." In the Save As menu, navigate to the folder, and hit save.

Doing terminal only commands,
1. sudo mkdir /etc/xinetd.d (if not already made)
2. cd /etc/xinetd.d
3. vi swat
4. Copy and paste contents
5. :wq <Enter>

---

### Post by Arisna on 2007-02-04
```
sudo nano -w *name of textfile*
```

You should be able to paste that in there, then use control key combinations to save.

---

### Post by nhandler on 2007-02-04
Another visual method using gedit:
gksudo gedit /etc/xinetd.d/swat

Paste the contents of the file, and then hit save.

---

