---
title: "What is root Password?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by sn00pd0gg1 on 2007-11-27
What is root password? can any1 explian to me whats that? idk what is it and I need it


:lolflag:

---

### Post by finer recliner on 2007-11-27
ubuntu doesnt provide one by default.

its recommended to use 'sudo' in front of any command that requires root privledges.
example:
```
 sudo pico /etc/X11/xorg.conf 
```

this will prompt you for a password, but its not the password for root, its the password for you current account

if you realllly need to be root, use this command:
```
sudo su
```

make sure you remember to log out as root user when you're done though.

---

### Post by Paul820 on 2007-11-27
This will explain all about root [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
You root password is the password you use when you log in to your system.

---

### Post by mjskia1 on 2007-11-27
The root password is what lets you make changes that affect your entire system in Linux.  Ubuntu uses a slightly different security model from most other versions of Linux; instead of using a root password, you use your own password through something called sudo.  So, if you're asked for a root password, just put in your own password.

Do be careful, though, because when you have root access, you can make a whole slew of changes that could be harmful.

---

