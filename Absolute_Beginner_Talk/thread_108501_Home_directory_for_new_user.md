---
title: "Home directory for new user"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by rensu on 2005-12-26
I got an error by creating a new user.
Could not chdir to home directory /home/test: No such file or directory
Anyone could tell me what could be wrong?

---

### Post by Nameless on 2005-12-26
[QUOTE=rensu]I got an error by creating a new user.
Could not chdir to home directory /home/test: No such file or directory
Anyone could tell me what could be wrong?[/QUOTE]

If I understand your question correctly, you are trying to make a new directory?

If so, I believe he command is mkdir, not chdir.

---

### Post by bagel on 2005-12-26
Try using *sudo adduser* instead of *sudo useradd*.

To delete users(**be careful**!)  use "sudo userdel".

By the way.. *cd* for changing directories

Ciao, 
bagel

---

### Post by odin on 2005-12-27
with adduser there is na option wher you can specify the home directory for the user.I think is just adduser --home "dir" but check the man page for this(type in the terminal "man adduser") to see all the options you have cause you can set whatever you want when you create the user

---

### Post by cjm5229 on 2005-12-27
If you can't get that to work, try just going to Systems>Adminidtration>Users and Groups. Or if you want to learn how to use "Terminal" Try this thread, [URL="http://www.ubuntuforums.org/showthread.php?t=73885"] It has some really good instructions. Carl

---

### Post by rensu on 2005-12-27
Thanks everyone! :)

---

