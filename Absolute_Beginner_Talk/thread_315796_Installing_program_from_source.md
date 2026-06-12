---
title: "Installing program from source"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by mr tim esquire on 2006-12-09
Im trying to install a program called c4.5
it was a .tar.gz file i used 'tar' to unstuff it then 'make all' to compile the source code now the install instructions tell me to move the executables to the directory 'bin' but when i try to do this the permissions are wrong whats the best way of moving the files?
thanks :)

---

### Post by smile_sunshine on 2006-12-09
Hi,
  

you can change the permsissions by typing in a terminal (from the folder they are in):

fairly sure it would be: 

> sudo chmod 755 <filename>     
 

but if not try

> sudo chmod 777 <filename> 

then try moving them again.

---

### Post by adaptr on 2006-12-09
Carefully re-read the instructions provided with the program.

For one thing, not many programs other than trivial one-file affairs use a preprovided makefile anymore; most projects use autoconf and will require you to run

#./configure

before you can make the project.

After that, most sane programs use the install utility to automatically install the resulting executables to the right locations, and set their permissions.

If none of the above seem present or funcitoning, you can just set executable permissions on the file yourself:

#chmod a+x filename && ./filename

Note that you cannot move files to /bin, and really, really should not, unless you know what you are doing.

---

### Post by smile_sunshine on 2006-12-09
just thought - do you mean the permissions for the files or that you don't have permission to move the files to /bin?   
but I think adaptr's advice is best :)

---

### Post by adaptr on 2006-12-10
> **smile_sunshine said:**
> just thought - do you mean the permissions for the files or that you don't have permission to move the files to /bin?
If he is doing this as a regular user then he does not have write permission to /bin.
Thankfully :)

---

### Post by lamego on 2006-12-10
install checkinstall and install the software with:
```
sudo checkinstall make install
```
This will make sure you can uninstall the software later from the software list.

---

### Post by CatKiller on 2006-12-10
Actually, just ```
sudo checkinstall
``` has worked better for me in the past.

The OP may want to read these links on permissions, since it's traditional:
[http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

