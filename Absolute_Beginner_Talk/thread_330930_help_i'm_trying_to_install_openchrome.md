---
title: "help i'm trying to install openchrome"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by uthturn on 2007-01-03
i'm obviously a complete noob but i've made it to this step:
Run autogen.sh with the prefix option so that the driver is being installed in the correct directory

./autogen.sh --prefix=/usr/

i can't find the right directory i guess i just don't know what i need to change and what the dir path would be . Sorry i'm a complete moron:confused:

---

### Post by taurus on 2007-01-03
I am sure you have to do something like

```
/autogen.sh
./configure --prefix=/usr
make
sudo make install
```

---

### Post by uthturn on 2007-01-03
it didn't work . i copy and paste the entire script into the terminal.
this is what happened
tj@tj-desktop:~/openchrome$ /autogen.sh
bash: /autogen.sh: No such file or directory
tj@tj-desktop:~/openchrome$ ./configure --prefix=/usr
bash: ./configure: No such file or directory
tj@tj-desktop:~/openchrome$ make
make: *** No targets specified and no makefile found.  Stop.
tj@tj-desktop:~/openchrome$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
tj@tj-desktop:~/openchrome$ ./configure --prefix=/usr
bash: ./configure: No such file or directory
tj@tj-desktop:~/openchrome$ 
god i know i'm doing something really noobish ](*,) 
thanks for the help:-D

---

### Post by taurus on 2007-01-03
```
./autogen.sh
./configure --prefix=/usr
make
sudo make install
```
Otherwise, paste the output of this command here.

```
ls -ls
```

---

### Post by uthturn on 2007-01-03
total 4
4 drwxr-xr-x 6 tj tj 4096 2007-01-03 21:20 trunk

---

### Post by taurus on 2007-01-03
I thought you want to build the openchrome!  It has only **trunk** directory under it!

```
ls -la ~/openchrome
```

---

### Post by uthturn on 2007-01-03
"I thought you want to build the openchrome! It has only trunk directory under it!"
did i mention i'm a moron i typed the command heres the result
total 12
drwxr-xr-x  3 tj tj 4096 2007-01-03 21:19 .
drwxr-xr-x 35 tj tj 4096 2007-01-03 21:19 ..
drwxr-xr-x  6 tj tj 4096 2007-01-03 21:20 trunk

---

### Post by taurus on 2007-01-03
```
ls -la ~/openchrome/trunk
```

---

### Post by uthturn on 2007-01-03
total 112
drwxr-xr-x 6 tj tj  4096 2007-01-03 21:20 .
drwxr-xr-x 3 tj tj  4096 2007-01-03 21:19 ..
-rw-r--r-- 1 tj tj  3766 2007-01-03 21:20 acinclude.m4
-rwxr-xr-x 1 tj tj   195 2007-01-03 21:20 autogen.sh
-rw-r--r-- 1 tj tj 47553 2007-01-03 21:20 ChangeLog
-rw-r--r-- 1 tj tj  5263 2007-01-03 21:20 configure.ac
drwxr-xr-x 3 tj tj  4096 2007-01-03 21:20 libxvmc
-rw-r--r-- 1 tj tj  1181 2007-01-03 21:20 Makefile.am
drwxr-xr-x 3 tj tj  4096 2007-01-03 21:20 man
-rwxr-xr-x 1 tj tj 18277 2007-01-03 21:20 prepare-ChangeLogSVN.pl
drwxr-xr-x 7 tj tj  4096 2007-01-03 21:20 .svn
drwxr-xr-x 3 tj tj  4096 2007-01-03 21:20 unichrome

---

### Post by taurus on 2007-01-03
So, you have to change directory into **trunk** before you can run those commands!!!

```
cd ~/openchrome/trunk
./autogen.sh
./configure --prefix=/usr
make
sudo make install
```
See if you get any error message (and from which command)!

---

### Post by uthturn on 2007-01-03
you are the man!!! :-D :-D :-D :-D thanks so much

---

### Post by taurus on 2007-01-03
> **uthturn said:**
> you are the man!!! :-D :-D :-D :-D thanks so much

I assume it works!!!

---

