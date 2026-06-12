---
title: "fail to run nautilus as root"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Harry789 on 2007-07-25
I tried to do gksudo nautilus and got a message that the underlying system does not allow me to run nautilus as root - contact system administrator - is this because i just logged in as ordinary user?

bt027la@laan97ac-laptop:/home/music$ gksudo nautilus
bt027la@laan97ac-laptop:/home/music$

---

### Post by Harry789 on 2007-07-25
Here I tried to log in as the first user I set up on the system

laan97ac@laan97ac-laptop:~$ gksudo nautilus
(nautilus:7736): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

While the nautilus window does come up I am wondering what to interpret from the message above.

---

### Post by Harry789 on 2007-07-25
This is driving me crazy!

laan97ac@laan97ac-laptop:~$ gksudo nautilus
(nautilus:8962): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

What on earth is this all about! ???

---

### Post by nhandler on 2007-07-25
You will get an error like that anytime you use gksudo. There isn't anything wrong, and the command will execute and run fine. Just ignore it.

---

### Post by Harry789 on 2007-07-25
well it does not execute because nautilus never comes up - nothing ever happens

trying from a different user login gives me this:

bella@laan97ac-laptop:~$ gksudo nautilus
GNOME_SUDO_PASS
sudo: 1 incorrect password attempt
GNOME_SUDO_PASS
sudo: 1 incorrect password attempt
GNOME_SUDO_PASS
sudo: 1 incorrect password attempt
bella@laan97ac-laptop:~$ 

and I swear i used the right password....

I am really confused.

---

