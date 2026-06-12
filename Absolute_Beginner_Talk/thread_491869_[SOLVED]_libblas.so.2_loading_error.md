---
title: "[SOLVED] libblas.so.2 loading error"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by sundol on 2007-07-04
I got a following error message while I ran areaimol of ccp4.

"areaimol: error while loading shared libraries: libblas.so.2: cannot open shared object file: No such file or directory"

However, libblas.so.3 exists.

Here is the result of "slocate libblas"
/usr/lib/atlas/libblas.so.3.0
/usr/lib/atlas/libblas.so.3


How can I solve this problem?

---

### Post by kevinlyfellow on 2007-07-04
you can try linking libblas.so.2 to libblas.so.3
```
sudo ln -s /usr/lib/atlas/libblas.so.2 /usr/lib/atlas/liblas.so.3
```

The repos don't have atlas2, which I guess is old.  If the above doesn't work, then maybe I can help you find a way to install atlas2

---

### Post by sundol on 2007-07-04
I tried your suggestion but it didn't work. 
also I found /usr/lib/libblas.so.3 and tried it, too but it didn't work, neither.

If I download altas2 package from older version of ubuntu and installed it, it will screw up with atlas3 ?

---

### Post by sundol on 2007-07-04
I found that atlas2 was supported until breezy and all of links doesn't exist. Help me to install the atlas2, please. :)

---

### Post by sundol on 2007-07-04
I downloaded atlas2 file from following link and installed it.
It works well now :)

Here is an alive link for atlas2
[ftp://ftp.uni-duesseldorf.de/pub/unix/linux/distributions/debian/pool/main/a/atlas/atlas2-base_3.2.1ln-15_i386.deb](ftp://ftp.uni-duesseldorf.de/pub/unix/linux/distributions/debian/pool/main/a/atlas/atlas2-base_3.2.1ln-15_i386.deb)

You may find other links to same file at
[http://www.filewatcher.com/m/atlas2-base_3.2.1ln-15_i386.deb.4189894.0.0.html](http://www.filewatcher.com/m/atlas2-base_3.2.1ln-15_i386.deb.4189894.0.0.html)

---

