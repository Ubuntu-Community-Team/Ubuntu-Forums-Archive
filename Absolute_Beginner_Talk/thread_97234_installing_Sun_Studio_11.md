---
title: "installing Sun Studio 11"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by Tails on 2005-11-30
hi.. just wonder to know, anyone installed the  Sun Studio 11 before?? 

becos, I tried to install and it does start the installer, but it couldnt install, as all the files are based rpm.. i also tried to use alien, but seems no luck at all.. :(
[http://www.sun.com/software/products/studio/index.xml](http://www.sun.com/software/products/studio/index.xml)

Thanks for helping...  :D

---

### Post by h4lfl1ng on 2006-01-26
I also need help with this same issue. I tried alien, but it gives errors.

---

### Post by h4lfl1ng on 2006-02-01
Bump! Anyone.

---

### Post by h4lfl1ng on 2006-02-20
Bump again.. :|

---

### Post by superhac007 on 2006-04-18
Sun Studio 11 Install on Ubuntu Breezy

# apt-get install libmotif3
# tar -xvf studio11-lin-x86.tar.bz2

# cd kits/ide/packages
# rm openmotif-2.1.31-3_IST.i386.rpm

--- if your not running AMD64
# rm -R sun-dbxx-11.0-1.x86_64.rpm
# rm -R sun-jdbxx-11.0-1.x86_64.rpm
# rm -R sun-prfax-11.0-1.x86_64.rpm
# rm -R sun-prflx-11.0-1.x86_64.rpm

--- Optionally you can remove all the files that contain the word "locale" if you only want the english version...
# rm  *locale*


# alien *
# dpkg -i *

---- Ignore last error message

-- to run
$ /opt/sun/sunstudio11/bin/sunstudio

---

### Post by h4lfl1ng on 2006-04-26
Thanks a bunch!

---

### Post by therealhannes on 2006-05-07
Cool, got it working too, but only with the --jdkhome option.
at the moment in can use it only as root. It tried to chmod 0777 all the bins but with no success. How can I run studio 11 as user?

---

