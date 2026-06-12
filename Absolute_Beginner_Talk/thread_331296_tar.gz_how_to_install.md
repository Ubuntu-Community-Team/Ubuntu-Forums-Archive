---
title: "tar.gz how to install"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by orangedangila on 2007-01-04
hi.. i tired to install kqemu.. but the file extension is tar.gz.. how to install it? i tried to configure first but i got some error massages... 

wahandoy@wahandoy-desktop:~/Desktop/kqemu-1.3.0pre9$ ./configure
Could not find kernel includes in /lib/modules or /usr/src/linux - cannot build the kqemu module
Source path       /home/wahandoy/Desktop/kqemu-1.3.0pre9
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
test: 347: yes: unexpected operator
wahandoy@wahandoy-desktop:~/Desktop/kqemu-1.3.0pre9$ make
make -C /usr/src/linux SUBDIRS=`pwd` modules
make: *** /usr/src/linux: No such file or directory.  Stop.
make: *** [kqemu.o] Error 2

any idea??

---

### Post by aysiu on 2007-01-04
If you're using Dapper (and not Edgy), you can try [this](http://www.ubuntuforums.org/showthread.php?t=187413).

---

### Post by jvc26 on 2007-01-04
Another helpful post is the one here - for installing most things:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Il

---

### Post by l3lackEyedAngels on 2007-01-16
That link is dead. :(

---

### Post by Canis familiaris on 2007-01-17
First install the build-essential package:
In terminal:
```
sudo aptitude install build-essential
```

Then to compile first untar in terminal, configure and make:
```
tar xvzf tarname.tar.gz
cd tarname
,/configure
make
sudo make install

```

---

### Post by xyz on 2007-01-17
Careful here...a little typo no doubt:
```
tar xvzf tarname.tar.gz
cd tarname
,/configure
make
sudo make install
```
It's:
```
tar xvzf tarname.tar.gz
cd tarname
./configure
make
sudo make install
```

**./configure** with a . not ,

---

### Post by 3rdalbum on 2007-01-17
I think the script is asking for your kernel headers - kqemu works by putting a special module into your kernel, so it needs the headers of the kernel in order to work out where to put itself.

The headers are available in the package "linux-headers", as long as you have the latest kernel from the repositories.

---

### Post by feest on 2007-01-17
almost every tar.gz files includes files for a standart prcedure, once you've downloaded de tar.gz. file (and installed all the requirements) you can start installing, switch to terminal and type

```
tar xvfz desktop/filename.tar.gz
```
to extract the file...

now we're gonna configure the package for installation
```
./configure
```

and now for the installation:
```
make install
```

---

### Post by xyz on 2007-01-17
I get nowhere with a small d:
```
tar xvfz desktop/filename.tar.gz
```
but this works for me:
```
tar xvfz Desktop/filename.tar.gz
```

---

### Post by wrinkle_Free on 2007-01-17
When I try to untar and try to do this step 

**```
./configure
```**

it always tell me 

> bash: ./configure: No such file or directory
 
what should i do ??

---

### Post by Ben Sprinkle on 2007-01-17
```

tar xvfz desktop/filename.tar.gz
sudo aptitude install build-essential

```
Try ./configure then ./make then ./make-install or ./make install

---

### Post by Ben Sprinkle on 2007-01-17
Or just make.

---

