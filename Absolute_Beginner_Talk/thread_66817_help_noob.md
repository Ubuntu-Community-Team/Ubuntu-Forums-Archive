---
title: "help noob"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by QDR06VV9 on 2005-09-18
hi i am ne tto kbuntu and don't have a  clue on how to install any of the packages i've d-loade from synapatic pkg mngr.
opened my menu but dont se any of them there?
oh and i did do a reboot :-?

---

### Post by bsussman on 2005-09-18
Upon clicking 'apply' Synaptic does install them if you chose install, rather than download only.

looking at the package in Synaptic, you can examine the list of installed files if the package doesn't include a menu item. Some packages do not. The thing to run will most likely be in /usr/bin or some other bin directory.

in a terminal you enter:

 ```
> type programname

or

> which programname

or

> whereis gimp

``` 
here is typical output:


 ```
bos@Dillon:~$ type gimp
gimp is /usr/bin/gimp
bos@Dillon:~$ which gimp
/usr/bin/gimp
bos@Dillon:~$ whereis gimp
gimp: /usr/bin/gimp /etc/gimp /usr/lib/gimp /usr/share/gimp /usr/share/man/man1/gimp.1.gz
bos@Dillon:~$
```

this means that to execute gimp, I merely need to:

 ```
> gimp
``` 

because it is in my path

---

