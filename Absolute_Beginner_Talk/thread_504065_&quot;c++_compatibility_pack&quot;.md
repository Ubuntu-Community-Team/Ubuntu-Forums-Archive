---
title: "&quot;c++ compatibility pack&quot;"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by bistro1 on 2007-07-18
Hello

I'm trying to install coldfusion 7.02 and some of the threads here were great to get me started, thank you. However, during installation I receive the message:

"The installer was unable to determine if the C++ compatibility pack is 
installed by running the following command: rpm --query compat-libstdc++
If this machine uses a version of glibc that is 2.2.5.x or higher the 
compatibility pack is necessary for C++ custom tags, Verity, and web server 
connectors to work properly."

I ignored this on my first install attempt but shouldn't have. I wonder if someone could advise me:
1. how to check what version of gilbc I have (assuming I have it at all) and
2. how to install the c++ compatibility pack if I need to.

Many thanks

Dave S

---

### Post by pyros on 2007-07-18
If you haven't installed it already, install the build-essential package.  After that you may want to take a look here:
[http://strivinglife.net/wordpress/2007/06/15/373/quickie-install-coldfusion-702-on-ubuntu-704-with-apache-224/](http://strivinglife.net/wordpress/2007/06/15/373/quickie-install-coldfusion-702-on-ubuntu-704-with-apache-224/)

---

### Post by bistro1 on 2007-07-18
Hi

thank you, the strivinglife.net advice is the same as a thread on here, but I still get the warning message.

---

### Post by pyros on 2007-07-19
well, looking at the error "by running the following command: rpm --query compat-libstdc++" it's attempting to run rpm, which is not a command that you will find on a debian-based system like ubuntu. I't will always give you that error.

---

