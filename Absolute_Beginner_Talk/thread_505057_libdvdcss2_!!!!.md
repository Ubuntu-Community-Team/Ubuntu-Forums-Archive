---
title: "libdvdcss2 !!!!"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by querent on 2007-07-19
libdvdcss2 is NOT available from synaptic package manager!

and at

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

the line

[https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)

is not recognized.  if this line is deleted, everything else detailed here works smoothly.  (bugs aren't reported, I suppose.)  this is madness.  someone help the children.

q

---

### Post by tgm4883 on 2007-07-19
> **querent said:**
> libdvdcss2 is NOT available from synaptic package manager!

and at

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

the line

[https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)

is not recognized.  if this line is deleted, everything else detailed here works smoothly.  (bugs aren't reported, I suppose.)  this is madness.  someone help the children.

q

that line should be in there.  looks like they forgot to comment it out.  Just the deb and deb-src lines should be in there.  Then do a apt-get update and try installing it again

---

### Post by deadlikeoscar on 2007-07-19
You don't want that line to be separate from the above line. It is supposed to be commented out with a # in front of it. If it is all one line you are okay. Just add a # in front of [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs) and leave the rest alone. You want the two lines AFTER that one to not be commented. Make sure if you are using Feisty that you modified those lines accordingly.

---

### Post by yabbadabbadont on 2007-07-19
```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```
:D

---

