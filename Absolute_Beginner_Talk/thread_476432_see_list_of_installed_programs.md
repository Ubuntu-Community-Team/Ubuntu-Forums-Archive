---
title: "see list of installed programs"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Irti on 2007-06-17
how can i see the list of installed programs i have on my comp......i mean add and remove is there...but it doesnt show up some of the programs i installed like opera (which is not there even in synaptics)

---

### Post by rekahsoft on 2007-06-17
open synaptic then go to the left panel and click "status" and then select "installed". This will not show programs that you have built from source but anything that you have installed by .deb will be there

---

### Post by scrooge_74 on 2007-06-17
Go to synaptic and you can check a list of everything that is install

---

### Post by schorsch on 2007-06-17
In a terminal you can use:

```
dpkg -l
```

and for checking if opera is installed:

```
dpkg -l|grep opera
```

This works without using sudo.

---

### Post by w4ett on 2007-06-17
There is a program called Debian Menu which will find and catagorize the apps on your system.  See here:

[http://www.arsgeek.com/?p=110](http://www.arsgeek.com/?p=110)

It's very useful.

---

### Post by zvacet on 2007-06-17
```
dpkg --get-selections > installed-software
```

and you will find file in your home folder with list of all installed softare

---

