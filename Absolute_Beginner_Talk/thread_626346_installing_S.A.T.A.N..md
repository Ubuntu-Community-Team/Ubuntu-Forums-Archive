---
title: "installing S.A.T.A.N."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by W33ZY_GHz on 2007-11-29
i can tfigure out how to install program that i downloaded called satan-1.1.1. any help?

---

### Post by jordanmthomas on 2007-11-29
1.  Download satan
2.  Right click on satan folder and go to extract here (I'm assuming on your Desktop)
3.  open a terminal
4.  type 
```
cd ~/Desktop/satan-1.1.1
```
5.  Then, you'll need to install a c compiler and netscape (maybe firefox will work instead of netscape, I don't really know)
```
sudo apt-get install build-essential
```
6.  To compile it, you'll want to type
```
./reconfig
```
This does not work for me, and it's likely dude to satan being absolutely ancient (The files in the tarball are from 1997)
Anyway, if this suceeds for you somehow, you can continue on to 
7. run this 
```
 make linux
```
which will also probably fail.
8.  run ./satan which will launch the web browser it finds.


Anyway, if I was you I wouldn't expect success.

---

