---
title: "gcc hello.c"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by koconnor100 on 2007-02-15
Got my hello world program. 
Got it to compile without errors (finally, after installing 30 megs of junk to make the gcc compiler work)

But it won't execute. 

I tried chmod u+x a.out to give it executable priviledges, and it shows it has the priviledges...but typing the file name gives only the message "bash: a.out: command not found"

ls -l on the directory gives ..

-rwxr-xr-x 1 kevin kevin 6627 2007-02-15 02:24 a.out
-rw-r--r-- 1 kevin kevin   69 2007-02-15 02:12 hello.c
-rwxr-xr-x 1 kevin kevin 6627 2007-02-15 02:25 hello.exe

I'm logged in as kevin

thanks in advance for any help.

---

### Post by mahy on 2007-02-15
you have to type ./a.out :)

---

### Post by yabbadabbadont on 2007-02-15
Edit: Too slow :D

---

### Post by koconnor100 on 2007-02-15
> **mahy said:**
> you have to type ./a.out :)


you're Sh*** me ? 

it worked by the way.

---

### Post by mahy on 2007-02-15
It's a way to tell bash not to look for a.out in the $PATH folders, but in the current directory instead. Don't worry, it took some time for me to find out, too.

---

