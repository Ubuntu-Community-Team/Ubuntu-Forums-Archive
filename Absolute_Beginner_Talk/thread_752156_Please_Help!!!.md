---
title: "Please Help!!!"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by ReZon4ce on 2008-04-11
PLEASE OH PLEASE help me install the development version of compiz fusion v0.7.4! Have have been trying to get it working for 3 full days and cant do it! the tuts a the wrost tuts in the world, im on this tut : [http://wiki.compiz-fusion.org/Installation](http://wiki.compiz-fusion.org/Installation)

So i installed all those things in the top box, next i clicked here : [http://releases.compiz-fusion.org/](http://releases.compiz-fusion.org/)

and chose 0.7.4

Next i do as it said and extracted all the files that had tar in the name on this page: [http://releases.compiz-fusion.org/0.7.4/](http://releases.compiz-fusion.org/0.7.4/)

and extracted them to my desktop.

Now on the next step where it says "To compile from the source tarballs, extract each tarball, then execute the following":

./autogen.sh --prefix=/usr/local
make
sudo make install 

And after that, i just get this! :

matthew@Matthewpc:~$ ./autogen.sh --prefix=/usr/local
bash: ./autogen.sh: No such file or directory
matthew@Matthewpc:~$ make
make: *** No targets specified and no makefile found. Stop.
matthew@Matthewpc:~$ sudo make install 




Please help me!

---

### Post by seshomaru samma on 2008-04-11
after you extract the tarball you need to CD to the directory 
so if the extracted tarball created a directory compiz-fusion-7.04 then you should run the command
```
cd compiz-fusion-7.04
```
(check the name of the actual directory by running the command "ls")


but why do you want to install the development version of compiz fusion?
it's installed by default in the newer versions of ubuntu....

---

### Post by hyper_ch on 2008-04-11
next time use a descriptive thread title and not a generic "need help" one.

---

