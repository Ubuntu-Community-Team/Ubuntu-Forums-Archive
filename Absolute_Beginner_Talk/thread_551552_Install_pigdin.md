---
title: "Install pigdin"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-09-15
hi, i have downloaded Pigdin 2.2.0 source, and want to install it.
I would realy appreciate if someone could give me a guid to how and say how they managed it (trying to learn terminal)

Please excuse my terrible English :(

---

### Post by Happy_Man on 2007-09-15
Well, first you have to extract to your /home directory. Right-click the extracted file and say "Extract here." (I'm assuming you extracted it to a folder on the Desktop.) Then, enter these commands in a terminal:

```
cd Desktop/<directory it made when you extracted it>
./configure
```

At the end, you may or may not see a list of packages that Pidgin needs as dependencies. If you do, go ahead and install them before moving on. In either case, once that's over, use the following commands: ```
make
sudo make install
```

It should work!

---

### Post by beyboo on 2007-09-15
I only prefer installing packages for the Ubuntu system using Synaptic / Add Remove or the Debian package manager. 

If you are just looking at having pidgin on your computer,  there is a 2.1.1 version available here ==> [http://www.getdeb.net/app.php?name=pidgin](http://www.getdeb.net/app.php?name=pidgin)

you have to download and install the packages in following order

pidgin-data_2.1.1-1~getdeb1_all.deb
pidgin_2.1.1-1~getdeb1_i386.deb

All you need to do after downloading them  is

I)  Right click the packages in nautilus and select  gdebi package manager 

2) or use the terminal 

#sudo gdebi  pidgin-data_2.1.1-1~getdeb1_all.deb
#sudo gdebi pidgin_2.1.1-1~getdeb1_i386.deb

---

### Post by Maestro23 on 2007-09-15
Make sure you have build-essential installed.

> sudo aptitude install build-essential

Compiling from source is not recommended it you are new to linux.  You will run into dependency hell as you have found out.  Always check the repos first for a program.

---

### Post by ajmannen on 2007-09-15
umm.. i tryed the first guid.  I came to the point where I had to write "make" now terminal is producing huge amounts of writing a cannot understand and have done so for 15 minuttes 
[[IMG]http://img517.imageshack.us/img517/5586/screenshotsi3.th.png[/IMG]](http://img517.imageshack.us/my.php?image=screenshotsi3.png)

---

### Post by meborc on 2007-09-15
the problem with installing from source is that it takes a loooong time to do so... i always use deb files if possible... download the getdeb 2 pidgin files to your home dir

then: ```
sudo dpkg -i pidgin*
``` and ```
sudo apt-get -f install
```as it has some dependencies and gives you an error after the first command

---

### Post by Happy_Man on 2007-09-15
> **ajmannen said:**
> umm.. i tryed the first guid.  I came to the point where I had to write "make" now terminal is producing huge amounts of writing a cannot understand and have done so for 15 minuttes 
[[IMG]http://img517.imageshack.us/img517/5586/screenshotsi3.th.png[/IMG]](http://img517.imageshack.us/my.php?image=screenshotsi3.png)
That's what it's supposed to do. It's called "compiling" and it takes forever.

---

