---
title: "Cannot Execute Binary file"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by sxturbo on 2006-03-19
I am learning how to work linux here, and Im having fun doing it. But i am having a fair share of issues.

I'm trying to install aMSN for my Ubuntu64 bit system. I download the correct file for this system and it just wont execute.

I tried 'sudo sh 'filename.bin' ' and all i get is 
'CANNOT EXECUTE BINARY FILE'
so i then went and tried "chmod +x 'filename.bin' " and then tried the previous sudo sh command and i still get the error. Any ideas guys?

---

### Post by KansasJoe on 2006-03-19
you can get that package through apt-get

sudo apt-get install amsn

if you want to compile and do it yourself then here's a wiki page for it
[http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installation+Instructions](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installation+Instructions)

---

### Post by sxturbo on 2006-03-19
I have the .94 version, but i was just trying to install the new .95 version. doing apt-get it wants to install .94.

its not a huge deal, it was just a good peice to practice installing something I downloaded. Im very new to this and trying different things to help me learn.\\:D/

---

### Post by KansasJoe on 2006-03-19
looks like you're gonna have to get some dependencies for it then....
    *  A working installation of tcl/tk version 8.3 or above. (8.4 is preferred)
    * A working installation of the tls module for tcl/tk (required since 0.83).
    * IMLib >= 1.8 for traydock support. 

then follow the link i put above and it will walk you through it...most of the work will be done with 

./configure
make
make install

make sure you have the build essentials before doing this

sudo apt-get install build-essential

---

