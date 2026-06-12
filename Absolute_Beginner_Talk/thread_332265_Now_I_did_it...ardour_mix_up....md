---
title: "Now I did it...ardour mix up..."
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-01-05
Well I tried to install Ardour through  synaptic, and figured out I need jack. So, I went to synaptic again, and installed jackd and a few other things I thought sounded useful...like jackrack and some other stuff. I try ardour, decide I don't like it, then go to remove the packages I installed. Now I'm stuck with this error in the terminal:

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Segmentation fault (core dumped)
Setting up cmt (1.15-3.1) ...
Segmentation fault (core dumped)
dpkg: error processing cmt (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 cmt
E: Sub-process /usr/bin/dpkg returned an error code (1)

when I try to install anything.
Any help is appreciated.

---

