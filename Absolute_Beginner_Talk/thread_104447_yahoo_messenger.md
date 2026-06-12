---
title: "yahoo messenger"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by leomps on 2005-12-16
Im trying to instal yahoo messenger...but its not happening.can anybody tell me how to do it..

Manpreet Singh.

---

### Post by 0okami on 2005-12-16
instructions can be found here: 
[http://messenger.yahoo.com/](http://messenger.yahoo.com/)

download: [http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb](http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb)
save it to your home dir. (default dir i believe it is) 

open a terminal window / console window and type:  
sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(if your not sure where the terminal window is, its applications->accessories->terminal)


After that, it should be installed. To run it, in a terminal type this: 
/usr/bin/ymessenger

---

### Post by leomps on 2005-12-16
[QUOTE=0okami]instructions can be found here: 
[http://messenger.yahoo.com/](http://messenger.yahoo.com/)

download: [http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb](http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb)
save it to your home dir. (default dir i believe it is) 

open a terminal window / console window and type:  
sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(if your not sure where the terminal window is, its applications->accessories->terminal)


After that, it should be installed. To run it, in a terminal type this: 
/usr/bin/ymessenger[/QUOTE]




im doing the same but it is saying no such file or directory found.

---

### Post by alamba on 2005-12-16
might not be on his path?? is that possible?

see what you get from: whereis ymessenger

then try /path_from_above/ymessenger

Akshay

---

### Post by leomps on 2005-12-16
When i try to instal i get following error..

(Reading database ... 56673 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger


please help me out..

Manpreet Singh.

---

### Post by codejunkie on 2005-12-16
[QUOTE=leomps]When i try to instal i get following error..

(Reading database ... 56673 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger


please help me out..

Manpreet Singh.[/QUOTE]
run ```
sudo apt-get -f install
``` and this will fix the dependency issues.

---

### Post by cstudent on 2005-12-16
Explained how to do it in this post:

[http://www.ubuntuforums.org/showthread.php?p=571672#post571672](http://www.ubuntuforums.org/showthread.php?p=571672#post571672)

---

### Post by jagguars on 2005-12-16
don't forget that you have kopete which can handle this protocol either and it is already on your box. 
this is in your internet folder as instant messanger.

mfg me

---

### Post by 0okami on 2005-12-16
also gaim handles yahoo messenger quite well and its already installed.

---

