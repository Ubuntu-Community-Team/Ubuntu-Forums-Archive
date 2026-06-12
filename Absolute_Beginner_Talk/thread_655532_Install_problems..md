---
title: "Install problems."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by 369gnl on 2008-01-01
Hi. Like Humpty newbie I too took the jump and got rid of windows and spent two days fiddeling about then I read the reply from snakeeyes  and went and went to the terminal and typed in the comand to instal ubuntu restricted extras worked ok but the it froze  so I tryed again and got the message -dpkg was interupted you must manually run  'dpkg--configure-a' to correct the problem  what is this and how do I do it hope you can help a green newbie :)

---

### Post by bapoumba on 2008-01-01
@ 369gnl: please run:
```
sudo dpkg --configure -a
```
and post the complete error message.

---

### Post by 369gnl on 2008-01-01
Thanks bapoumba that worked, so I started over and it is stuck at the same spot :( it seams to be the  sun- java6-jre at the moment I feel that I want to sort this out later when I have a bit more understanding.
The reast works ok, all i would like to do is be able to set up so I can see streaming that are sent using wmp and mplayer seams to be the one I need but when I try to sat it as my default player movie player wont let it.
Can anybody help? 
glad that I got ride of windows you guys are great

---

### Post by bapoumba on 2008-01-01
> **369gnl said:**
> Thanks bapoumba that worked, so I started over and it is stuck at the same spot :( it seams to be the  sun- java6-jre at the moment I feel that I want to sort this out later when I have a bit more understanding.
Did you accept the license during the install process? 

> **369gnl said:**
> 
The reast works ok, all i would like to do is be able to set up so I can see streaming that are sent using wmp and mplayer seams to be the one I need but when I try to sat it as my default player movie player wont let it.
Can anybody help? 
glad that I got ride of windows you guys are great
I'm not much into multimedia. I've installed **vlc** for my son and he could figure out how to use it (he is 13).

---

### Post by 369gnl on 2008-01-01
Yes the next time should i not?

---

### Post by bapoumba on 2008-01-01
I've split your posts from the previous thread to its own.
Yes, the license has to be accepted. Can you please post the complete error message?

---

### Post by 369gnl on 2008-01-01
Yes I will but it will be tomorrow or wednesday as i can hardly see at the moment :) too long in front of the computer.

---

### Post by 369gnl on 2008-01-02
Hi here goes 
Opend the terminal and typed in  sudo dpkg-help  alist came up as follows

dpkg--help for help about installing and deinstalling packages [*]
use 'dselect' or 'aptitude' for user-friendly package management
type dpkg-Dhelp for a list of forcing options
type dpkg-deb-help for help about manipulating*. deb files
type dpkg--license for copyright license and lack of warranty (GNU GPL 0 [*]

options marked(*) produce a lot of out put-pipe it through 'less' or 'more'  

The above is what happend after i had tryed the 

sudo dpkg-- configure-a  

having read all of the above I am alittle confused so I do hope you can help


thanks a lot and a :)from me 369gnl

---

### Post by jken146 on 2008-01-02
You typed it in wrong.  It should be ```
sudo dpkg --configure -a
```
Watch where the spaces are and the dashes.

---

### Post by 369gnl on 2008-01-02
just re typed the comand and the last line is ;-

ldconfig deferred processing now taking place:-
then my name-desktop:- $ and the flashing curser
how long should I wait?

---

### Post by bapoumba on 2008-01-04
If there is no error when you get the prompt back, you should be all good.

---

