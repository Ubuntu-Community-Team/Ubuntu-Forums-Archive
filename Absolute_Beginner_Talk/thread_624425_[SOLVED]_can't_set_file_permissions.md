---
title: "[SOLVED] can't set file permissions"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2007-11-26
I tried to write a tiny bash script to run espeak and greet me when I turn my computer on, heh.
Anyway I get this output when I try to set permissions the way I think I want them:

private@private-laptop:~$ sudo chmod -rwxr-xr-x /home/private/greeting.sh
chmod: /home/private/greeting.sh: new permissions are ----w----, not ---------
private@private-laptop:~$ sudo chmod -x /home/private/greeting.sh
private@private-laptop:~$ sudo chmod -rwxr-xr-x /home/private/greeting.sh
chmod: /home/private/greeting.sh: new permissions are ----w----, not ---------
private@private-laptop:~$ 

Am I doing something wrong?

---

### Post by meatpan on 2007-11-27
You are close, but the paramater supplied to chmod is not correctly formatted.  In the permission specification string, you must indicate if you are changing owner, group, or other permissions (basically, the extra '-' fields you use are are incorrect)
So, in your first example, try:
```
sudo chmod u=rwx,go=rx /home/private/greeting.sh
```
Note:  group and other have been combined into 'go' for brevity.

Just for reference, in the string -rwxr-xr-x, each consecutive group of three characters after the first '-', corresponds to user, group, and other.

Here is a handy tutorial, if you want some more info:
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by spiderbatdad on 2007-11-27
Thank you.

---

