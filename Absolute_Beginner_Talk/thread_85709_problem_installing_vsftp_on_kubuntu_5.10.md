---
title: "problem installing vsftp on kubuntu 5.10"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by ilalina on 2005-11-03
HI!

I am new to LINUX (using Kubuntu 5.10) so this might be a really basic issue. I need to install a ftp daemon and downloaded vsftpd-2.0.3, unpacked and followed the instructions in the INSTALL file. Got stucked on step 1(!!) when trying to build vsftpd and don't really understand why. Typed "make" and got lots of error and warning messages, and the whole thing ended with:

make: *** [sysutil.o] Error 1

I guess there are some configurations I need to do? 

Greatful for any input!

---

### Post by frodon on 2005-11-03
I don't know what is your need about ftp server, but if your goal is to share files with your friends i wrote a [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=79588") about it.
I use proftpd to do it.

Good luck ;)

---

### Post by ilalina on 2005-11-03
[QUOTE=frodon]I don't know what is your need about ftp server, but if your goal is to share files with your friends i wrote a [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=79588") about it.
I use proftpd to do it.

Good luck ;)[/QUOTE]
My primary need for a ftp server is to move files between my unix and my pc. 

Thanks!

---

### Post by LHZ on 2005-11-03
Did you 

> sudo apt-get install build-essential

at some point in time? This gives you all the compilers and libraries needed to compile stuff locally.

---

### Post by ilalina on 2005-11-03
Thought I did so allready but obviously not. I got some help from people here so I guess I didn't really follow what they did (and didn't) do. 

Now it seems to be working fine. Thanks a lot!!

---

### Post by ilalina on 2005-11-04
Back again :-)

It worked fine to install vsftpd and run the binary but when I tried to connect this happened:

$ ftp localhost
Connected to localhost.localdomain.
500 OOPS: vsftpd: cannot locate user specified in 'ftp_username':ftp

Does anyone know what this means?

THANKS!!

---

