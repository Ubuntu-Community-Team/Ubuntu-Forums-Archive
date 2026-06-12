---
title: "Package install error"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by mysticrider92 on 2006-08-30
I am trying to install the glib-2.12.2 package using terminal. I used cd to get to the folder it is in and ran the ./configure command and this worked fine. The problem is, when I try to run the "make" command I get this error: 

> desktop:~/Desktop/glib-2.12.2$ make
bash: make: command not found 

I tried it with sudo, and I get almost the same error. ](*,) I have also tried a few other packages and the same thing happens. Any ideas?


Sorry if this is in the wrong place.

---

### Post by XAsmodeanX on 2006-08-30
Type:

sudo apt-get install build-essential make

---

### Post by mysticrider92 on 2006-08-30
Thank you! :-D

---

