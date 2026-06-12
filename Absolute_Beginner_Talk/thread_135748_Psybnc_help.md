---
title: "Psybnc help"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by Preparedtoolz on 2006-02-24
Hey guys! I'm pretty new in ubuntu linux :-) And this is my first post yeah! 

Today when I tried to fix psybnc on ubuntu linux I just got error codes such as;

johan@zerver:~/psybnc $ make menuconfig
Initializing Menu-Configuration[*] Running Conversion Tool for older psyBNC Data.
make: gcc: Command not found
make: *** [menuconfig] Error 127

I've checked that the "make" commando is installed etc. Whats the problem?

Thankful for helping!

---

### Post by Gcool on 2006-02-24
Try installing gcc

---

### Post by madmonk3y on 2007-06-12
[http://ubuntuforums.org/showpost.php?p=2829953&postcount=1](http://ubuntuforums.org/showpost.php?p=2829953&postcount=1)

Try the above link.  If you still want to install PsyBNC knowing that and why it won't work correctly, here's the packages you need to be able to make menuconfig and have the compile complete (with warnings and future instability):

[http://ubuntuforums.org/showpost.php?p=2830116&postcount=5](http://ubuntuforums.org/showpost.php?p=2830116&postcount=5)

---

