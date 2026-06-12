---
title: "installing gstreamer0.8-mad?"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by dcast on 2005-10-24
I use hoary 5.04. My linux machine isn't connected so I downloaded gstreamer on my windows box and transported it to ubuntu and just put it on the desktop. Unforunately I have no idea how to install it from here. How would I do this?
thanks

---

### Post by mostwanted on 2005-10-24
$ dkpg -i myPackage.deb

Should do the trick. Be sure to be inside the directoru where the deb is, or use an absolute path.

---

### Post by Kyral on 2005-10-24
I'm assuming they got downloaded as .deb files?

If that is the case just open a terminal and navigate to where they are (If you need a primer in the Terminal checkout the link below) and

```
sudo dpkg -i <filename>
```

For each package

---

### Post by dcast on 2005-10-24
I did download as a .deb I tried as you said but got this response

sudo dpkg -i gstreamer0.8-mad_0.8.8-2_i386.deb
dpkg: error processing gstreamer0.8-mad_0.8.8-2_i386.deb (--install):
 cannot access archive: no such file or directory
errors were encountered while processing 
 gstreamer0.8-mad_0.8.8-2_i386.deb

---

### Post by Kyral on 2005-10-24
You have to be "in" the directory where it is

---

### Post by dcast on 2005-10-24
sorry but what do you mean exactly im extremely new to linux

---

### Post by Kyral on 2005-10-24
Read this and it will be clear *Mystic kinda sounds*

[http://www.ubuntuforums.org/showthread.php?p=402620](http://www.ubuntuforums.org/showthread.php?p=402620)

---

### Post by dcast on 2005-10-24
Thanks a lot, this helped but apparently the package is dependant on some other packages which are not installed so i will work on those
thanks very much

---

