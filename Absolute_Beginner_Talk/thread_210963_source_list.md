---
title: "source list"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-07
I used to have permission to access my source list via terminal
/etc/apt/sources.list 

that is correct right??

Then i would also open my source list using text editor and it wouldnt allow me permission to save changes.

Can anyone tell me why i suddenly lost permission??

---

### Post by crystal on 2006-07-07
You need to use sudo.

---

### Post by Tiede on 2006-07-07
are you sure you are using ```
sudo gedit /etc/apt/sources.list
```
If you do not use sudo, it will not open it for editing.
Also, if your system's administrator took away your name away from the sudoers file, you will not be allowed to do anything requiring those privileges.

---

### Post by IrishGangsta on 2006-07-07
ohhhh
thanx yea i forgot sudo, still learning the command line thing...

---

### Post by crystal on 2006-07-07
> If you do not use sudo, it will not open it.
Probably should be able to read (and hence open) it, but not able to write (and hence save) to it.

---

### Post by richbarna on 2006-07-07
Actually it's safer to use gksudo for gnome and kdesu with kde, when opening graphical programs.

Have a read of this :-
[http://www.psychocats.net/ubuntu/graphicalsudo.php](http://www.psychocats.net/ubuntu/graphicalsudo.php)

---

### Post by IrishGangsta on 2006-07-07
It works
I FORGOT SUDO
thank you to everyone who is helping but you can stop adding to this now
thank you
haha

---

