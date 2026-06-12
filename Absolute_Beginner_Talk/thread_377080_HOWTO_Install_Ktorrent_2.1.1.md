---
title: "HOWTO: Install Ktorrent 2.1.1"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by maynoth on 2007-03-05
Hello everyone...

I would like to share with you how I got ktorrent 2.1.1 running in Edgy.

I know they have debs for the older 2.1 version but I wanted the newest available.

The instructions on Ktorrent's site as well as in the .gz file are don't seem to help much for regular ubuntu edgy, I had to teach myself how to do this.

Big thanks to all the ppl esp (chavo, bonbonthejon, renze) in #ubuntu/#kubuntu.

I hope this helps someone please let me know how it works out for you, if you can help me improve these instructions please let me know.

**_Prior To Installation:**_

[color=red]The Ktorrent Devs Suggest Running:[/color]
```
make -f admin/Makefile.common
```

Prior To Running:
```
./configure --prefix=$(kde-config --prefix)
```

Doing so on Ubuntu 6.10 requires you to install "build-essential" "automake" "autoconf" "kde-devel" "kdelib" 

I am not sure what is really necessary so just use synaptic and just grab everything related to those packages before doing anything else.  I personally know this fixes a bug with the ip-filter plug-in not being able to unzip the splist.zip, it may fix other bugs also.  





_**Install:**_

1. Download and Copy ktorrent-2.1.1.tar.gz to home directory [http://ktorrent.org/downloads/2.1.1/ktorrent-2.1.1.tar.gz]("http://ktorrent.org/downloads/2.1.1/ktorrent-2.1.1.tar.gz")

2. ```
tar -xvzf ktorrent-2.1.1.tar.gz
```

3. ```
cd ktorrent-2.1.1
```

4. ```
sudo apt-get build-dep ktorrent
```

5. ```
make -f admin/Makefile.common
```

6. ```
./configure --prefix=$(kde-config --prefix)
```

7. ```
sudo apt-get install unsermake
```

8. ```
unsermake
```

9. ```
sudo unsermake install
```

10. ```
which ktorrent 
``` (tells you where its installed)

11.```
sudo chmod 777 (insert data from above here, it was "/usr/bin/ktorrent" for me)
```




_**Uninstall:**_

1. ```
cd ktorrent-2.1.1
```

2. ```
sudo unsermake uninstall
```




_**Run From Terminal:**_

```
ktorrent
```





_**Create Launcher:**_

```
ktorrent
```

Icon is in the home directory /ktorrent-2.1.1/apps/ktorrent/hi128-app-ktorrent.png


_**P.S.**_

If for some weird reason you get errors when trying to launch ktorrent without check to make sure your have write permissions for the directory listed in the terminal error messages. (sudo nautilus)

---

### Post by maynoth on 2007-03-05
If anyone can help me improve these instructions please let me know... I am still a n00b.

---

### Post by lodp on 2007-03-06
somebody has made a .deb package for ktorrent 2.1 (has also been posted in the dl section of ktorrent.org), makes things a whole lot easier:

```
wget http://buntudot.org/people/~jdong/ktorrent/2.1/ktorrent_2.1-0ubuntu1~6.10prevu1_i386.deb
```

```

sudo dpkg -i ktorrent_2.1-0ubuntu1~6.10prevu1_i386.deb

```

...and you're set. at least for version 2.1 -- 2.1.1 hasn't been packaged yet (but it's mostly a bugfix release anyway).

---

### Post by maynoth on 2007-03-06
lodp, 

Thanks..  I just like running current software.  I absolutely hate running old software.  I try to keep all the software i use current.    I just thought this guide might help some who like running the latest also.

---

### Post by maynoth on 2007-03-06
Could anyone help me make this into a .deb? checkinstall crashes to cli and saying to use unsermake instead...

---

