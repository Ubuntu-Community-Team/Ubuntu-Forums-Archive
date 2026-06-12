---
title: "[SOLVED] msttcorefonts error when using synaptic/apt-get"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2008-01-04
```
E: msttcorefonts: subprocess post-installation script returned error exit status 1
```

There was an error in the 'terminal' box in synaptic that said something about a file being locked, I couldnt copy the message though.

I have tried un-installing and reinstalling 'restricted extras' but get the same error. The error happens now whenever I use synaptic or apt-get.

I caused it by forcing synaptic to quit before it had finished installing 'restricted extras', I forced it because it wasnt connecting to one of the sourceforge servers.


I tried this
> 
:~$ sudo dpkg --configure -a
Setting up msttcorefonts (2.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts



EDIT
I fixed it by using 'sudo rm' on the locked files.

---

