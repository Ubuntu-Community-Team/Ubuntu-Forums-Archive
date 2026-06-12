---
title: "How do I install programmes manually"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by Tamatoa on 2006-06-18
#-o   If you don't have Internet access, but can download the occasional package or have a CD with packages, how do you actually go about installing a package and its dependencies manually?

Any help would be greatly appreciated.

I actually need to install g++ 3.4 at the moment.

Cheers

---

### Post by simon_is_learning on 2006-06-18
If you have it on a CD you just adds the CD-rom to the sources.list, but thats if its a precompiled package..

Otherwise if it's a question of source program then you'll first need to have build-essentials
then you can put the program on a floppy or USB memory and then compile it on your computer...

---

### Post by deadgobby on 2006-06-18
[QUOTE=Tamatoa]#-o   If you don't have Internet access, but can download the occasional package or have a CD with packages, how do you actually go about installing a package and its dependencies manually?

Any help would be greatly appreciated.

I actually need to install g++ 3.4 at the moment.

Cheers[/QUOTE]
[https://wiki.ubuntu.com/PackageCDs?highlight=%28cd%29](https://wiki.ubuntu.com/PackageCDs?highlight=%28cd%29)
[http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/)
I hope this is what you are looking for.

---

### Post by harishg on 2006-06-18
The usual way is open a root terminal and go the the directiory and type 
./configure 
make 
make install

and if the dependencies are missing it will tell you what are you missing.

---

### Post by mostwanted on 2006-06-18
This is probably the info that you want:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Goes through all the popular methods of installing software on Ubuntu.

---

