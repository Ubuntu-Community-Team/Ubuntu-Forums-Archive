---
title: "Previous user problem"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by ufa on 2005-07-23
Hi all,
I used to have a Linux installed with RaiserFS with 2 partititions: "/" and "/home" . I formated and installed Ubuntu in "/" and i wish to reuse the users in "/home", so i just created the same users on Ubuntu system. But when i log with a previous existing user, it brings me a error, saying that i do not have access (writing permission denied). How can i fix it, without chmod 777 * -R?

---

### Post by Xian on 2005-07-23
$ sudo chown -R user:user /home/user/
If you need then set the file perms to 751 or 755.

---

