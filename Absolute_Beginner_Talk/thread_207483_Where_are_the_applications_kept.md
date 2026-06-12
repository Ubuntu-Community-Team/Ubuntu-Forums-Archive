---
title: "Where are the applications kept?"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by drosophyllum on 2006-07-01
I am trying to manually/terminal install a program and it is asking me what directory to install itself, so ive tried to look for the actuall place the applications are stored, with no success

So does anyone know where the applications are stored?

I did find something i think might be it- 
/usr/bin 
it has binaries with the applications names but i doubt this is it.

sorry if this is a noob question :oops:

---

### Post by scxtt on 2006-07-01
most are in /bin (main system ones) - /usr/bin seems like a logical place ... there is no "right" place - you can put them whereever you want ... some programs default to certain "expected" directories, but you should be fine w/ /usr/bin ...

---

### Post by mlind on 2006-07-01
If you're going through configure && make && make install route,
it's common to install those under /usr/local for global use (other users)
or if it's just for yourself then you can use prefix $HOME.

---

### Post by David_T on 2006-07-01
Hi,
    Yes it is usually /usr/bin, but have you tried getting the application through synaptic or apt-get?

---

### Post by someusernoob on 2006-07-01
Open a terminal and type:

```

man hier

```

to get a complete overview of the file system hierarchy, so you can go figure out where to put all the files you want to install.

I know there is a shorter version of man hier somewhere on the internet (with the most common dirs explained) but can not find it.

---

### Post by richbarna on 2006-07-01
[QUOTE=David_T]Hi,
    Yes it is usually /usr/bin, but have you tried getting the application through synaptic or apt-get?[/QUOTE]

I agree with David_T, try and find the program you need in Synaptic, if it's not there and you still have problems with your install, post again and we'll help you out.

One thing to remember if you are manually installing is to get the build-essential  package which provides you with the tools you need to do an ./configure, make, sudo make install.

In the terminal type :-

> sudo apt-get install build-essential

---

### Post by 3rdalbum on 2006-07-02
If it's asking you where to install the program, and it doesn't provide a default, then it's probably able to be installed into your home directory and "run in place". For instance, the game Alien Arena allows you to do that, as do most Python-based programs.

But /usr/bin is a good place to put it.

---

