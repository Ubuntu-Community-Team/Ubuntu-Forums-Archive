---
title: "moving, copying files"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Kid G on 2006-01-28
Hi, I want to copy the file *libgpod-1.0.pc.in* to the folder *usr/local/lib/pkgconfig* but I get a message saying I dont have permission - how is this achieved? (I need the terminal command).

Thanks

---

### Post by bscbrit on 2006-01-28
Prefix the command with 'sudo' - when it asks for your password simply give it your normal user password.

---

### Post by Kid G on 2006-01-28
Sorry I'm a complete newbie at this,

What is the structure of the move command -
sudo ? filename?

Thanks

---

### Post by psomas on 2006-01-28
sudo lets you act as if being the root...
now for moving files: mv source destination (type man mv in the terminal and you will see its syntax)
for copying cp file1 file2
so you write: sudo cp file file2
then you give your password and the files are copied

---

### Post by Kid G on 2006-01-28
Hi again!

I'm getting this message:

gary@ubuntu:~/libgpod-0.3.0$ sudo cp libgpod-1.0.pc.in usr/local/lib/pkgconfig
cp: cannot create regular file `usr/local/lib/pkgconfig': No such file or directory

ligpod-0.30 is in my home folder and contains the file l*ibgpod-1.0.pc.in* Do I need to change how I've stated the path for the destination folder?

Thanks (again)

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=Kid G]Hi again!

I'm getting this message:

gary@ubuntu:~/libgpod-0.3.0$ sudo cp libgpod-1.0.pc.in usr/local/lib/pkgconfig
cp: cannot create regular file `usr/local/lib/pkgconfig': No such file or directory

ligpod-0.30 is in my home folder and contains the file l*ibgpod-1.0.pc.in* Do I need to change how I've stated the path for the destination folder?

Thanks (again)[/QUOTE]

You probably need to start with the initial slash (e.g. **/**usr/local/lib/pkgconfig)

---

### Post by Kid G on 2006-01-28
That is it! :o 

Thanks

---

