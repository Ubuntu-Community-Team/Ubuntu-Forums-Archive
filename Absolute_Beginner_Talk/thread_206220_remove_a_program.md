---
title: "remove a program"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by evaristegalois on 2006-06-29
How do you remove a program that you don't want any more? (installed from source, not using Debian or Synaptic)

--evaristegalois

---

### Post by Maggot on 2006-06-29
Obviously you'd have to find out what files directory's it created.  What program was it?

---

### Post by uzi09 on 2006-06-29
manually. as in search for all directories and files and delete them. even then you'll probably have stuff remaining from it. this is why you should avoid compiling it :(

the easiest way is to just type:
locate program_name
and it'll give you a bunch of files/directories.
then sit down, make sure it's a directory actually created by the program and not just another directory which happens to have the same name and remove each and every file/folder.

that's the best way i know, anyone else is welcome to jump in

---

### Post by Maggot on 2006-06-29
I also believe it creates a log file which lists the files/directory's. So I guess you could manually install it again :D

---

