---
title: "Getting error when compiling Hyperserv"
date: 2012-12-26
forum: Any Other OS
---

### Post by fetz on 2012-12-26
```
[ 17%] Built target sauertools
[ 64%] Built target enet
make[2]: *** No rule to make target `/usr/libpython2.6.so', needed by `src/hyperserv'.  Stop.
make[1]: *** [src/CMakeFiles/hyperserv.dir/all] Error 2
make: *** [all] Error 2

```


How can i fix this? (Am on debian, but is super similar...)

---

### Post by fetz on 2012-12-26
Here is the site with the readme and stuff


[https://github.com/amstan/hyperserv](https://github.com/amstan/hyperserv)

---

### Post by Cheesemill on 2012-12-26
Have you installed all of the dependencies? It looks like you are missing libpython.
```
sudo apt-get install libpython2.6
```

---

### Post by fetz on 2012-12-26
hyperserv@debian:/usr/lib/python2.6/config$ sudo apt-get install libpython2.6
[sudo] password for hyperserv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpython2.6 is already the newest version.
libpython2.6 set to manually installed.
The following packages were automatically installed and are no longer required:
  iso-codes python3.1 python3.1-minimal python3 python3-minimal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hyperserv@debian:/usr/lib/python2.6/config$

---

### Post by ranger1021994 on 2012-12-26
> **fetz said:**
> hyperserv@debian:/usr/lib/python2.6/config$ sudo apt-get install libpython2.6
[sudo] password for hyperserv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpython2.6 is already the newest version.
libpython2.6 set to manually installed.
The following packages were automatically installed and are no longer required:
  iso-codes python3.1 python3.1-minimal python3 python3-minimal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hyperserv@debian:/usr/lib/python2.6/config$

Try installing python development files for 2.6

---

### Post by fetz on 2012-12-26
hyperserv@debian:/usr/lib/python2.6/config$ sudo apt-get install python2.6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.6-dev is already the newest version.
python2.6-dev set to manually installed.
The following packages were automatically installed and are no longer required:
  iso-codes python3.1 python3.1-minimal python3 python3-minimal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hyperserv@debian:/usr/lib/python2.6/config$ 


Somone told me this but i dunno what it means:

libpython somewhat like /usr/lib/python2.6/config/libpython2.6.so, not /usr/libpython2.6.so
pure_ascii
2) you shouldn't have to build it together with hyerserv, it should be there already from the OS
pure_ascii
guess u need to install python-2.6 and python-2.5-devel and tell hyperserv where it is

What does this mean>

---

### Post by oldos2er on 2012-12-26
Moved to Other OS/Distro Talk.

---

### Post by fetz on 2012-12-26
K.

---

### Post by ranger1021994 on 2012-12-26
> **fetz said:**
> hyperserv@debian:/usr/lib/python2.6/config$ sudo apt-get install python2.6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.6-dev is already the newest version.
python2.6-dev set to manually installed.
The following packages were automatically installed and are no longer required:
  iso-codes python3.1 python3.1-minimal python3 python3-minimal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hyperserv@debian:/usr/lib/python2.6/config$ 


Somone told me this but i dunno what it means:

libpython somewhat like /usr/lib/python2.6/config/libpython2.6.so, not /usr/libpython2.6.so
pure_ascii
2) you shouldn't have to build it together with hyerserv, it should be there already from the OS
pure_ascii
guess u need to install python-2.6 and python-2.5-devel and tell hyperserv where it is

What does this mean>

Do one thing..
Copy libpython2.6.so to /usr .
Its simpler than editing source code by yourself

---

### Post by fetz on 2012-12-26
hyperserv@debian:/usr$ ls
bin    include  lib64            local       sbin   src
games  lib      libpython2.6.so  lost+found  share
hyperserv@debian:/usr$ 


Already in there... but highlighted: in black with red lettars

---

### Post by fetz on 2012-12-26
Is that bad?

---

