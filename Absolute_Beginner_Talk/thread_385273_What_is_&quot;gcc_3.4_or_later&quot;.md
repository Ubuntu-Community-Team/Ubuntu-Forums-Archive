---
title: "What is &quot;gcc 3.4 or later?&quot;"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by paker on 2007-03-15
I am buying an Epson scanner V100. From google, I found AVASYS site for various Linux drivers. For the scanner I have choose between "gcc 3.4 or later" and "gcc 3.2 and 3.3" I have Ubuntu Edgy 6.10 32 bit. Which one must I download? Thanks.

One more question. They have both RPM package and source file available. Which one should I download?

---

### Post by lamalex on 2007-03-15
do
```
apt-get install build-essential
``` and that will get you newest version of gcc. You will want source package. Ubuntu does not support RPM packages

---

### Post by ashmew2 on 2007-03-15
GCC is the C compiler under Ubuntu (a s far as i know) . I think the later the version the better..

---

### Post by ashmew2 on 2007-03-15
GCC is the C compiler under Ubuntu (a s far as i know) . I think the later the version the better..and as far as rpm and source is concerned..installing from source would be much better as rpm are not native packages (they are Red Hat Packages) , but if installing from source gives u any problems , u can always use alien to install from an rpm.

---

### Post by kelbizzle on 2007-03-15
GCC is the Gnu Compiler Collectiion. Some software need to be compile first because there some values that change depending on the system. 

```
sudo apt-get install build-essential
``` will give you most of the software needed to compile stuff.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) number 4 on this page tells a little bit more about it.

---

### Post by adam s on 2007-03-15
If you can find a .deb file it will be easier.

.deb is the native file for debian systems. Ubuntu is a debian version of Linux.

Adam.

---

### Post by paker on 2007-03-15
Thanks for the relies.
1) The site does not have .deb file.
2) Thanks for the link, item 4. It has all the instructions I will need, I think.
3) Thanks for explaining rpm package. I came across "alien" and was wondering what it was. 

I hope installation goes breeze. Thanks.

---

