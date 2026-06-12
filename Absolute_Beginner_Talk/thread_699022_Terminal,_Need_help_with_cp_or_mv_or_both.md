---
title: "Terminal, Need help with cp or mv or both?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Sugi on 2008-02-16
I know this is a really simple question and I should know it, but I don't :-/    How do I copy a directory in the terminal to another spot?

cp /home/user/a/bob/ /home/user/b/
> cp: omitting directory
mv /home/user/a/bob/ /home/user/b/
mv moves the whole thing, but I want to copy to directory /b/ (mv = move  yea, i get it >.<)

How do i copy directories?


Sugi

---

### Post by JoshuaRL on 2008-02-16
Try these following two links.  The first one is for "cp", the second for "mv".

[http://www.linuxcommand.org/lts0050.php#cp](http://www.linuxcommand.org/lts0050.php#cp)

[http://www.linuxcommand.org/lts0050.php#mv](http://www.linuxcommand.org/lts0050.php#mv)

I believe you want cp.  Something like:

```

co -r /home/user/a/bob/ /home/user/b/

```
should do it.

---

### Post by TheBoat on 2008-02-16
```
cp -r *source destination*
```This will copy recursively, meaning the directory and everything inside of it.

---

### Post by freddyp on 2008-02-16
Here's a simple one page Linux users guide that might help with some basic commands

[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

---

