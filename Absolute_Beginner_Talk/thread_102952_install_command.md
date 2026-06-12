---
title: "install command"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by xstation on 2005-12-13
I am trying to install two prorams but having difficulty



fist proramme:cool: 


andy108@heis:~/Desktop$ cd kylixlibs3-borqt
andy108@heis:~/Desktop/kylixlibs3-borqt$ sudo ./install.sh
Password:
grep: /etc/ld.so.conf: No such file or directory
andy108@heis:~/Desktop/kylixlibs3-borqt$



second programme


andy108@heis:/home$ cd ./easybreezy-install
andy108@heis:/home/easybreezy-install$ ./install
bash: ./install: Permission denied
andy108@heis:/home/easybreezy-install$ sudo ./install
Password:
sudo: ./install: command not found
andy108@heis:/home/easybreezy-install$ ./install.sh
bash: ./install.sh: No such file or directory
andy108@heis:/home/easybreezy-install$ ./install easybreezy-installbash: ./install: Permission denied
andy108@heis:/home/easybreezy-install$ sudo ./install easybreezy-installsudo: ./install: command not found
andy108@heis:/home/easybreezy-install$


:smile: :smile: 
can someone give the correct command line for the above --I think in the first
install there is something  missing?


andy

---

### Post by sonny on 2005-12-13
For the first one you are right there's something missing, and is you ld.so library wich gives you thee ld.so.conf file, first search in the repo's if there's something like that, if you can't find anything then do some google for it at [www.google.com/linux](www.google.com/linux).

For the second I've no idea what are you trying to run, please open a console in the directory easybreezy-install and type: ls -la

because I don't understand what file are you trying to run.

---

### Post by xstation on 2005-12-13
Here are the files in the easybreezy-install directory.

/home/easybreezy-install/conf
/home/easybreezy-install/autoscript.amd64
/home/easybreezy-install/autoscript.ppc
/home/easybreezy-install/autoscript.x86
/home/easybreezy-install/changelog
/home/easybreezy-install/EasyBreezy
/home/easybreezy-install/gpl.txt
/home/easybreezy-install/install
/home/easybreezy-install/README
/home/easybreezy-install/uninstall


andy:(

---

### Post by JimmyBEng on 2005-12-13
Is the install file executable? I don't know if that might matter.
```
chmod u+x install
```

---

### Post by xstation on 2005-12-14
ndy108@heis:/home$ cd ./easybreezy-install
andy108@heis:/home/easybreezy-install$ chmod u+x install
chmod: changing permissions of `install': Operation not permitted
andy108@heis:/home/easybreezy-install$ sudo chmod u+x install
Password:
andy108@heis:/home/easybreezy-install$ sudo chmod u+x install
andy108@heis:/home/easybreezy-install$ sudo install
install: too few arguments
Try `install --help' for more information.
andy108@heis:/home/easybreezy-install$ sudo install easybreezy-install
install: too few arguments
Try `install --help' for more information.
andy108@heis:/home/easybreezy-install$



any comments please

andrew:smile: :smile:

---

### Post by sonny on 2005-12-15
please type in your command line: ls -la

---

### Post by xstation on 2005-12-15
command line output


andy108@heis:/home/easybreezy-install$ ls -la
total 128
drwxr-xr-x  3 root root  4096 2005-12-10 14:01 .
drwxr-xr-x  6 root root  4096 2005-12-13 23:48 ..
-rw-r--r--  1 root root 26164 2005-12-06 02:53 autoscript.amd64
-rw-r--r--  1 root root 18307 2005-12-06 03:57 autoscript.ppc
-rw-r--r--  1 root root 26444 2005-12-06 02:56 autoscript.x86
-rw-r--r--  1 root root   772 2005-12-06 03:56 changelog
drwxr-xr-x  7 root root  4096 2005-12-10 14:01 conf
-rw-r--r--  1 root root  2713 2005-12-05 08:36 EasyBreezy
-rw-r--r--  1 root root 18011 2005-08-16 15:14 gpl.txt
-rwxr--r--  1 root root  3299 2005-12-04 08:24 install
-rw-r--r--  1 root root   275 2005-11-24 15:02 README
-rw-r--r--  1 root root  1584 2005-12-04 08:24 uninstall
andy108@heis:/home/easybreezy-install$



andy:smile: :smile:

---

### Post by robotgeek on 2005-12-15
All you need to do is:
> 
cd easybreezy-install
chmod +x install
./install


---

### Post by robotgeek on 2005-12-15
[QUOTE=xstation]command line output


andy108@heis:/home/easybreezy-install$ ls -la
total 128
drwxr-xr-x  3 root root  4096 2005-12-10 14:01 .
drwxr-xr-x  6 root root  4096 2005-12-13 23:48 ..
-rw-r--r--  1 root root 26164 2005-12-06 02:53 autoscript.amd64
-rw-r--r--  1 root root 18307 2005-12-06 03:57 autoscript.ppc
-rw-r--r--  1 root root 26444 2005-12-06 02:56 autoscript.x86
-rw-r--r--  1 root root   772 2005-12-06 03:56 changelog
drwxr-xr-x  7 root root  4096 2005-12-10 14:01 conf
-rw-r--r--  1 root root  2713 2005-12-05 08:36 EasyBreezy
-rw-r--r--  1 root root 18011 2005-08-16 15:14 gpl.txt
-rwxr--r--  1 root root  3299 2005-12-04 08:24 install
-rw-r--r--  1 root root   275 2005-11-24 15:02 README
-rw-r--r--  1 root root  1584 2005-12-04 08:24 uninstall
andy108@heis:/home/easybreezy-install$



andy:smile: :smile:[/QUOTE]

You seem to have installed it in some weird place. Please do the following in a terminal to install it correctly. 
> cd 
wget -c [http://www.giannaros.org/buntu/easybreezy-latest.tar.gz](http://www.giannaros.org/buntu/easybreezy-latest.tar.gz)
tar -zxf easybreezy-latest.tar.gz
cd easybreezy-install
./install

---

