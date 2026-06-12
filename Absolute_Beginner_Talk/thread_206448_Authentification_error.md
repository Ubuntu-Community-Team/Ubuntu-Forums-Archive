---
title: "Authentification error"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by J0E0NE on 2006-06-30
When I try to gain root access in a terminal, this happens:
joe@joe-desktop:~$ su
Password:
su: Authentication failure
Sorry.

I have tried many times and know the password is right as it works everywhere else, login synaptics etc...

How can I fix this?

Thanks in advance for all of your help.

---

### Post by woedend on 2006-06-30
by default, sudo is used, su isn't.  sudo is a way of giving a user temporary root priveleges without actually using a root account.  By default the root password is set to randomly generate, youll never know what it is.  You can do one of three things
a) just use sudo, it works fine
b) use 'sudo su', which will put you in the same place, and accept the user password
c) use sudo su, then push enter, then type passwd to set a new root password....really not needed....but after this point su will work with this new password.

---

### Post by ajgreeny on 2006-06-30
If you want root access to a gui prog, however, use gksudo in gnome or kdesu in kde, eg *gksudo gedit* or *kdesu konqueror*.  If you use sudo it is just possible to mess up your system, not likely perhaps but possible, so better safe than sorry.

---

### Post by ovimunt on 2006-06-30
A brute force way to work as root is this

>  sudo -s 

However this is NOT recommended!!!

---

### Post by J0E0NE on 2006-06-30
No ill just use sudo, thx all :)

---

