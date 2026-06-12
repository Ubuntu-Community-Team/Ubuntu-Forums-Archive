---
title: "Help on Ubuntu Equivalent Commands..."
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by oragon on 2005-09-19
Hello Gurus!

Before im using mandrake desktop-based linux, now im switching to Ubuntu Linux 5.04. Somebody help me find or what is the equivalent commands and other encountered situations of Ubuntu on a redhat-based linux, such as;

1. checking running services (like chkconfig on redhat/mandrake)
2. restarting services
3. after uncompressing tar.bz and tar.gzip files, do i have to compile that application    
before running it? when will i used the command ./configure? (im not more on compiling linux packages)
4. i always encounter problems with libraries on Ubuntu, such installing gDesklets, looking for XML/PERl parser, python libs... where this is already installed.

Thanks for your support!

---

### Post by Xian on 2005-09-19
[QUOTE=oragon]
2. restarting services
3. after uncompressing tar.bz and tar.gzip files, do i have to compile that application    
before running it? when will i used the command ./configure? (im not more on compiling linux packages)
4. i always encounter problems with libraries on Ubuntu, such installing gDesklets, looking for XML/PERl parser, python libs... where this is already installed.[/QUOTE]
2. a. # sudo invoke-rc.d <servicename> restart
b. # sudo /etc/init.d/<servicename> restart
3. You mean a source file tarball? Yes.
4. a. Install the gdesklets file in Synaptic. 
b. # sudo apt-get build-dep <packagename>

---

### Post by oragon on 2005-09-19
Thanks Xian, i really appreciate your support!

---

