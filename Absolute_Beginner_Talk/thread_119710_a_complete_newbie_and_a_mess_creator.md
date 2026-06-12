---
title: "a complete newbie and a mess creator"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by anurag_gupta on 2006-01-20
i think i hav accidently messed up the synaptic package manger. now any of the options in the adminstaration menu doesn't works it just shows the busy mouse cursor for few seconds an dnothing happens.
i also activated the  internet account by using networking option in the admin. but nothing happened. the modem is not recongnized by the os. i tried installing modem drivers but it said u should have superuser privilleges. what is that? and now whenever i start ubuntu 5.10 an error occurs saying

" could not connect to internet for. this will prevent GNOME from working properly. this may be solved by editing /etc/hosts."

the above message is not exactly the same as.

plz help.

i foend that breezy doesn't have gcc,c++or any c/c++ compiler installed.

---

### Post by darth_vector on 2006-01-20
your /etc/hosts file should have the following entry:

127.0.0.1       localhost.localdomain   localhost       <your computer name>

if it doesnt, you should fix this```
sudo gedit /etc/hosts
```
to install a C and C++ compiler, plus all the headers and so forth run```
sudo apt-get install build-essential
```

---

### Post by public_void on 2006-01-20
To get the c/c++ compiler etc you have to "sudo apt-get install build-essentials" in the terminal. But you don't seem to have internet access, so that will have to wait. I think it could be the case of a win modem.

> ...but it said u should have superuser privilleges. what is that?
Superuser or root privilleges allow you to have access to the whole system like in Windows. You don't have this privillege by default because it is somewhat of a security risk allowing a user (and applications running under that user) access to the whole system. Because of this it is less likely that a under privillege user (or virus, although thats not really a worry, but in theory) upsetthing the system.

---

### Post by darth_vector on 2006-01-20
[QUOTE=anurag_gupta]i think i hav accidently messed up the synaptic package manger. now any of the options in the adminstaration menu doesn't works it just shows the busy mouse cursor for few seconds an dnothing happens.[/QUOTE]

use aptitude. to update your system```
sudo apt-get update
sudo apt-get dist-upgrade
```
to search for a package```
sudo apt-cache search <programname>
```
to install```
sudo apt-get install <programname>
```

---

