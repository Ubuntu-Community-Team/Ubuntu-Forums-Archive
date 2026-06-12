---
title: "Basic basic question: how to create a user?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Tones on 2006-10-23
I'm an Ubuntu/Linux noob running an Ubuntu server install, so am command-line only. The only reference I can find in the Ubuntu documentation to creating a new user is in [the Desktop manual]("https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html"), which requires the GUI 'Users And Groups application'.

Can anyone point me to the right documentation page for creating and managing my ubuntu users over the command-line?

The goal is to allow others to SSH or FTP onto the server using their own accounts.

Thanks!

=T=

---

### Post by taurus on 2006-10-23
```

sudo useradd -m -s /bin/bash john
sudo passwd john

```

---

### Post by tonyr on 2006-10-23
**useradd** is one of a set of low level user administration tools:
**useradd**, **groupadd**, and **usermod**.  There is a more
friendly front end, **adduser** (also **addgroup**).  There
are man pages for all of these.

---

### Post by grim918 on 2006-10-23
Do you know if adduser still works. example:

```
sudo adduser john
passwd john
```

im just curious to know. Im not on my ubuntu box so I can't check:D

---

### Post by az on 2006-10-23
emma@ubuntu:~$ sudo adduser question
Password:
Adding user `question'...
Adding new group `question' (1002).
Adding new user `question' (1002) with group `question'.
Creating home directory `/home/question'.
Copying files from `/etc/skel'
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for question
Enter the new value, or press ENTER for the default
        Full Name []: question person
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [y/N] y
emma@ubuntu:~$

---

### Post by maaronB on 2006-10-23
You can do it in Gnome by going to System -> Administration -> Users and Groups -> Users -> Add User

---

### Post by AndyCooll on 2006-10-23
> **maaronB said:**
> You can do it in Gnome by going to System -> Administration -> Users and Groups -> Users -> Add User

Normally yes, however OP indicated that he was using a server and hence only the command line was available.

:cool:

---

### Post by sumguy231 on 2006-10-23
> **maaronB said:**
> You can do it in Gnome by going to System -> Administration -> Users and Groups -> Users -> Add User

But that's rather difficult when you don't have X installed. ;)

---

