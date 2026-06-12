---
title: "Gnome PPX"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Snitz on 2008-03-28
[http://www.gnomefiles.org/app.php/GNOME_PPX](http://www.gnomefiles.org/app.php/GNOME_PPX)

Can this be found as .deb file so I can install it on ubuntu?
I really need it to be able to make a pppoe connection with a service name.

---

### Post by clarknova on 2008-03-28
I don't see any debs for it but you can try installing alien and then in a terminal 'sudo alien -c gnome-ppx-0.6.1-1.i386.rpm'. This will create a deb file that you can try installing.

db

---

### Post by Snitz on 2008-03-28
I got the following error

> sudo alien -c gnome-ppx-0.6.1-1.i386.rpm

---

### Post by talsemgeest on 2008-03-28
Just download the autopackage installer.

---

### Post by Snitz on 2008-03-28
I'm installing the alien module now, hope it works.

---

### Post by Snitz on 2008-03-28
I downloaded the "Alien" module and ran the command, now I got this error.

> Must run as root to convert to deb format (or you may use fakeroot).

---

### Post by Snitz on 2008-03-28
Now I'm getting this,

> 
slevin@slevin-laptop:~$ sudo alien -c gnome-ppx-0.6.1-1.i386.rpm
File "gnome-ppx-0.6.1-1.i386.rpm" not found.
slevin@slevin-laptop:~$ sudu alien -c '/home/slevin/Desktop/gnome-ppx-0.6.1-1.i386.rpm'
bash: sudu: command not found



---

### Post by talsemgeest on 2008-03-28
Sudo, not sudu

---

### Post by Snitz on 2008-03-28
I got this one

> 
slevin@slevin-laptop:~$ sudo alien -c '/home/slevin/Desktop/gnome-ppx-0.6.1-1.i386.rpm'
mkdir: cannot create directory `gnome-ppx-0.6.1': File exists
unable to mkdir gnome-ppx-0.6.1:  at /usr/share/perl5/Alien/Package.pm line 257.


---

### Post by talsemgeest on 2008-03-28
Means the file is allready there, so delete it.

---

### Post by Snitz on 2008-03-28
Hehe, so confusing.

> File "/home/slevin/Desktop/gnome-ppx-0.6.1-1.i386.rpm" not found.

---

### Post by Snitz on 2008-03-28
I'm trying to delete the gnome-ppx folder found in /home/Slevin but it sayins access denied.

---

### Post by talsemgeest on 2008-03-28
Go ```
 gksudo nautilus
``` and delete whatever you need.

---

