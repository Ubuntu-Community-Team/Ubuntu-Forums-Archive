---
title: "problem accessing files"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-04-04
I can't access some files even when I login with my root password. I get a permission denied message. ?

---

### Post by fdrake on 2007-04-04
open the terminal
cd <path files>
sudo chmod 755 <file>  #this make the file executable and readable to any user. only the owner can change it.

---

### Post by woodsonoversoul on 2007-04-04
OK, I mean I'm trying to copy over a file and can't. I can look at the file. When I enter the chmod command, it ask for my password and accepts it, then still won't let me copy over this file...

---

### Post by fdrake on 2007-04-04
ok then try this.
sudo chown <your_username> <filename>
sudo chmod 775 <filename>

---

### Post by woodsonoversoul on 2007-04-04
Thanks fdrake, that worked perfect. What exactly did I just do?

---

### Post by fdrake on 2007-04-04
chown (changes the owner of the file), 
chmod 775 (change the permisions of the file):

users____________permissions
owner___________7=rwe=read , write, execute
owner's group___7=rwe=read , write, execute
everyone else____5=re=read, execute

it doesn't matter if you are root or another super user if your not the owner of that file or don't belong to the owner's group you won't be able to change it.
now that you changed the owner , that file belongs to you.

---

