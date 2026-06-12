---
title: "fedora guru / ubuntu newbie needs help"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by ewaguespack on 2006-04-17
I have quite a bit of experience with red hat, but I have yet to figure out the following in ubuntu:


= how do I "init 3" ? that is how do I kill xwindows?

= how do I do an "rpm -qf /path/to/file"? using apt-get / dpkg

= finally, how do I do a "yum search 'keyword'"


Thanks

---

### Post by Sutekh on 2006-04-17
I think these are equivalents for you...

[QUOTE=ewaguespack]I have quite a bit of experience with red hat, but I have yet to figure out the following in ubuntu:


= how do I "init 3" ? that is how do I kill xwindows?[/quote]```
sudo /etc/init.d/gdm stop
```

[quote=ewaguespack]
= how do I do an "rpm -qf /path/to/file"? using apt-get / dpkg
[/quote]```
sudo dpkg -i /path/to/file
```to install a .deb package that you have downloaded or```
sudo apt-get install <packagename>
```to install a package from the online repositories

[quote=ewaguespack]
= finally, how do I do a "yum search 'keyword'"


Thanks[/QUOTE]```
sudo apt-cache search "keyword"
```
then use ```
sudo apt-get install "keyword"
```to install what you want.

---

### Post by ewaguespack on 2006-04-17
nice... thanks for the quick reply

---

### Post by Sutekh on 2006-04-17
Welcome, did the first one achieve what you wanted? I wasn't quite sure if that's what you were asking.

To start the display manager again use
```
sudo /etc/init.d/gdm restart
```

---

### Post by ewaguespack on 2006-04-17
yes, that was exactly what I was looking for, basically I like to kill xwindows sometimes to save resources and kill the gui... thanks again.

---

### Post by Sutekh on 2006-04-17
Not a problem!

---

### Post by mostwanted on 2006-04-17
[QUOTE=ewaguespack]yes, that was exactly what I was looking for, basically I like to kill xwindows sometimes to save resources and kill the gui... thanks again.[/QUOTE]

if you just want to restart X you can do a Ctrl + Alt + Shift

---

