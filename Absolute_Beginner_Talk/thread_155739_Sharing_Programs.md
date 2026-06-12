---
title: "Sharing Programs"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by NGDanny on 2006-04-05
Hi,

I installed DDPoker as root.  The program works fine when I log-in as root.
but when I log-in as user ( no admin rights) I can't get the programs to run.

Is there a way to make a single program available to all users?

Danny

Linux is Fun!!!]](*,)

---

### Post by localzuk on 2006-04-05
How did you install it?

You may need to run ```
sudo chmod a+x path/to/app
``` in order to give other user permissions.

---

### Post by NGDanny on 2006-04-05
localzuk,

I download the program from the DDPoker web site.  I followed their installation instructions.  Had to add a usr/lib file and make an adjustment with the "Save" directory.  After that DDPoker ran fine when I log in as root.

Danny

---

