---
title: "MadWIfi make error"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Pete89 on 2007-02-15
Hello everyone,

I am a real begginer when it comes to LINUX. There is no doubt. And I have no problems asking what may seem like stupid questions. I am determined to leave my old operating system because I was tired of clicking away without knowing what I was doing. Yes, I want to know what I am doing and I want to really own my OS.

I am starting to get into penatration testing and the best platform for that is LINUX. I want to link to the documentation I am using for this project


[http://www.pauldotcom.com/KarmaUbuntu.pdf](http://www.pauldotcom.com/KarmaUbuntu.pdf)

To get Karma up and running I need to manully install MadWifi. After I get everyting downloaded and installed. I try and run *make* from /madwifi and I get this:

```
Makefile.inc:113: *** KERNELPATH: /usr/src/linux-2.6.15-26-386 does not exist. Stop.
```

So I assume I need to get a copy the source kernel files in the usr/src/linux-2.6.15-26-386
directory. 

_Question 1. _Is this assuption correct?

OK I then downloaded this file to the /usr/src directory:

linux-image-2.6.15-28-386_2.6.15-28.51_i386.deb

_Question 2._ Is this the right file for the source kernel?

I expanded it and it left me with this in the /usr/src directory:

control.tar.gz
linux-image-2.6.15-28-386_2.6.15-28.51_i386.deb
data.tar.gz
debian-binary
linux-headers-2.6.15-26-386 (this one was already there)
linux-headers-2.6.15-26 (this one too)


So I now create the directory the make commands wants in the error message (linux-2.6.15-26-386) and copy the results of the expanded .deb in there. I expand the two tar files and now I have this in the /usr/src/linux-2.6.15-26-386 directory:

boot
control
control.tar.gz
data.tar.gz
debian-binary
lib
postinst
postrm
preinst
prerm
usr

I then try to run the make command for MadWifi and I get this:

```
Makefile.inc:139: *** KERNELCONF: /usr/src/linux-2.6.15-28-386/.config does not exist..  Stop.
```

I am doing something wrong but I dont know what to do next.

Any help will be very apprecited,

Pete

---

### Post by dstew on 2007-02-15
It seems that madwifi is looking for the .config file that was used to compile the kernel. You can show the linux "hidden" files (those whose names begin with a "dot" character) by using ls -a.

---

