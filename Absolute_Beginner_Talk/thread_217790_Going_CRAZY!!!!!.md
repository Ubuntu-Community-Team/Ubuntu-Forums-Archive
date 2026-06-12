---
title: "Going CRAZY!!!!!"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Indian_rebel on 2006-07-17
Ok folks, I decide that i am going to install stratagus 2.1 and so i download the .deb version...it then tells me that i need a file called stratagus-data which i dutifully download.....that tells me i need stratagus 2.1 which is the first file i set out to download in the first place but wasnt able to execute coz i did not have data....in other words i am going round in circles!!!!!!!!HELP!!!!!!

---

### Post by T700 on 2006-07-17
Are you getting these error messages while trying to download?  During the installation process?  Have you checked on the site from which you are downloading program for a FAQ or the like?  Lastly, is this in the repositories?  If so, that's a much easier way to download and install it.

More details+Descriptive Title-Excess Exclamation Points=Better Answers

Paul

---

### Post by Indian_rebel on 2006-07-17
[http://packages.ubuntu.com/dapper/games/stratagus](http://packages.ubuntu.com/dapper/games/stratagus) thats where i downloaded the file from..... on finishing the download i opened the .deb file with GDebi package installer....when i ran stratagus-gl.deb it gave me a error saying that "Error: Dependency is not satisfiable: stratagus-data.
So i went back and downloaded the dependency stratagus-data(file called bos)again a .deb extension. On running GDebi....it gave me the following error "Error: Dependency not satisfiable: stratagus-gl"
In short stratagus-data will not install till stratagus gl is installed and stratagus gl will not install till stratagus-data is installed......

---

### Post by T700 on 2006-07-17
Make sure that repository is enabled in your source.list file and then at a terminal, type:

```
sudo aptitude update
``` 
Enter

```
sudo aptitude install stratagus
```

Enter

And see if that installs it.

Paul

---

### Post by taurus on 2006-07-17
Try to install it from a terminal, Applications -> Accessories -> Terminal, to see if you get the same error message!

```

cd ~/Desktop (I assume that's where you save your downloads...)
sudo dpkg -i stratagus-gl.deb
sudo dpkg -i stratagus-data.deb

```

---

### Post by Indian_rebel on 2006-07-17
job@ubuntu:~/Desktop$ sudo dpkg -i stratagus_2.1-8_i386.deb
(Reading database ... 69994 files and directories currently installed.)
Preparing to replace stratagus 2.1-8 (using stratagus_2.1-8_i386.deb) ...
Unpacking replacement stratagus ...
dpkg: dependency problems prevent configuration of stratagus:
 stratagus depends on stratagus-data; however:
  Package stratagus-data is not installed.
dpkg: error processing stratagus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 stratagus
job@ubuntu:~/Desktop$ sudo dpkg -i bos_1.1-3_all.deb
Selecting previously deselected package bos.
(Reading database ... 69994 files and directories currently installed.)
Unpacking bos (from bos_1.1-3_all.deb) ...
dpkg: dependency problems prevent configuration of bos:
 bos depends on stratagus (>= 2.1) | stratagus-gl (>= 2.1); however:
  Package stratagus is not configured yet.
  Package stratagus-gl is not installed.
dpkg: error processing bos (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
thats the errors i got!!!!

---

### Post by jimrz on 2006-07-17
> **T700 said:**
> Make sure that repository is enabled in your source.list file and then at a terminal, type:

```
sudo aptitude update
``` 
Enter

```
sudo aptitude install stratagus
```

Enter

And see if that installs it.

Paul

both stratagus & stratagus-gl (OpenGL) v.2.1-8 are in the universe repo [make sure you have it enabled]. Do the above and let aptitude handle the dependency issue for you, or just simply use Synaptic.

---

