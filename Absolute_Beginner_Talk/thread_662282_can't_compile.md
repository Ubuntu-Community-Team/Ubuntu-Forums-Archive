---
title: "can't compile"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by metalpancake on 2008-01-08
I am trying to compile pidgin using this tutorial:[http://neoaddict.wordpress.com/2007/10/01/compile-pidgin-221-from-source-in-ubuntu/]("http://neoaddict.wordpress.com/2007/10/01/compile-pidgin-221-from-source-in-ubuntu/")
when I get to: ```
./configure –prefix=/usr/local –enable-gnutls=yes
```
The terminal breaks this news to me:```
bash: ./configure: No such file or directory

```
any ideas? :confused:

---

### Post by dcstar on 2008-01-08
> **metalpancake said:**
> I am trying to compile pidgin using this tutorial:[http://neoaddict.wordpress.com/2007/10/01/compile-pidgin-221-from-source-in-ubuntu/]("http://neoaddict.wordpress.com/2007/10/01/compile-pidgin-221-from-source-in-ubuntu/")
when I get to: ```
./configure –prefix=/usr/local –enable-gnutls=yes
```
The terminal breaks this news to me:```
bash: ./configure: No such file or directory

```
any ideas? :confused:

You have not followed the instructions exactly, otherwise you would be in the directory where you have extracted all the files - including the "configure" one.

---

### Post by metalpancake on 2008-01-08
I extracted the files to desktop, so is that what I should change the terminal directory to?

---

### Post by FriedChips on 2008-01-08
if you type "ls" in the console you should see a "configure" file if you don't your in the wrong directory. If you downloaded the source to the desktop in a folder called Pidgin the commands to get to configure would be.
```
cd $HOME/Desktop/Pidgin
./configure
```
or just
```
cd Desktop/Pidgin
./configure
```
should work too if you just opened the terminal

---

### Post by FriedChips on 2008-01-08
Just curious though why are you compiling pidgin when you could install it with
```
sudo apt-get install pidgin
```
I assume you want a newer version or something??

---

