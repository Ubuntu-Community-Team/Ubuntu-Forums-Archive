---
title: "ls output question"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by indigoshift on 2006-10-25
Quick question:

When I do an "ls -l" I get a lot of information.  I understand all of it except for one thing:

```
drwxr-xr-x  3 indigoshift indigoshift   4096 2006-10-22 12:03 backgrounds

```

What does that "3" after the permissions indicate?

---

### Post by CatKiller on 2006-10-25
Isn't that the number of files that link to that file? Or something similar, anyway.

---

### Post by lloyd_b on 2006-10-25
> What does that "3" after the permissions indicate?

I have no clue what the correct terminology for this is, but if you "cd" into that directory, and do an "ls -la *", you'll note that there are 3 directory entries.

This is true for all directories.  That number = 2 + number of subdirectories (the 2 comes from the "." and ".." directories).

Lloyd B.

---

### Post by bodhi.zazen on 2006-10-25
The number 3 is the number of hard links to the file. Example:

> bodhi@ubuntu:~$ touch test
bodhi@ubuntu:~$ ll | grep test
-rw-r--r--  **[color=red]1**[/color] bodhi adm           0 2006-10-24 23:18 test
bodhi@ubuntu:~$ ln test test1
bodhi@ubuntu:~$ ll | grep test
-rw-r--r--  **[color=green]2**[/color] bodhi adm           0 2006-10-24 23:18 test
-rw-r--r--  **[color=green]2**[/color] bodhi adm           0 2006-10-24 23:18 test1
bodhi@ubuntu:~$ 

_Note_: the number increased form 1 to 2 after the hard link.

_Note_: [color=navy]alias ll='ls -la --color=auto'[/color]

[Understanding Links](http://wiki.linuxquestions.org/wiki/Symlink)

---

### Post by indigoshift on 2006-10-25
Thanks!  I've always wondered what that number was for. :D

---

### Post by bodhi.zazen on 2006-10-25
For directories the number "3" is NOT the number of hard links (as is is with a file), rather it is the number directories within the directory itself. The default number is going to always be 2 because of the . and .. directories.

> bodhi@ubuntu:~$ mkdir test
bodhi@ubuntu:~$ ll | grep test
drwxr-xr-x  **[color=red]2**[/color] bodhi adm        4096 2006-10-24 23:46 test
bodhi@ubuntu:~$ mkdir test/dir_in_test
bodhi@ubuntu:~$ ll | grep test
drwxr-xr-x  **[color=green]3**[/color] bodhi adm        4096 2006-10-24 23:46 test
bodhi@ubuntu:~$

---

