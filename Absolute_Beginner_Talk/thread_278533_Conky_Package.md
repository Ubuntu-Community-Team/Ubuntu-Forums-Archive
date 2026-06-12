---
title: "Conky Package"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by dodge78 on 2006-10-16
Hi there,
I'm having a problem trying to get the Conky package every time I apt-get I get as follows:

sudo apt-get install conky
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package conky

I have ubuntu dapper 2.6.15-27-386, and I have updated apt-get. 
Does the pakage excist anymore? if yes or no, how can i get the pakg?

---

### Post by taurus on 2006-10-16
Make sure you have both universe & multiverse in your /etc/apt/sources.list.  You can do that by editing your /etc/apt/sources.list and removing the # in front of those lines...

```
gksudo gedit /etc/apt/sources.list
```
Then,

```

sudo aptitude update
sudo aptitude install conky

```

---

### Post by dodge78 on 2006-10-16
thanks for the help it worked perfectly. i didnt even think to take out the # in the list. got it downloaded :-D

---

### Post by taurus on 2006-10-16
Glad to help.  If you need a sample ~/.tormrc, you can check out this site and download the one that you like.  Then, modify it to whatever you want...

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

