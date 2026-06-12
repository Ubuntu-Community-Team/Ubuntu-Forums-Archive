---
title: "g++ install"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by JO68 on 2007-11-29
Long story short, I'm an ultra noob, I've had Ubuntu 7.10 on my laptop for all of 3 days and it is my first time using anything other than Windows. I'm trying to install and get Kismet running (school project, trying to crack WEP) but i need to first get g++ working.  I have a friend in another country who was helping me a bit today but he had to get to bed.  So we got to a point where it seemed as if I would be able to install Kismet but then:

*** WARNING ***
LibPCAP was not found.  Kismet previously included a local copy of this
library, however it now expects libpcap to be provided by the system.
Kismet on Linux without LibPcap cannot capture data locally and will 
almost certainly NOT BE WHAT YOU WANT.
Your distribution should provide packages for libpcap, otherwise 
it can be downloaded from [http://tcpdump.org](http://tcpdump.org)

Configuration complete.  Run 'make dep' to generate dependencies
and 'make' followed by 'make install' to compile and install.
jordan@Jordan-Ubuntu:~/Desktop/Kismet/kismet-2007-10-R1$ make dep
Makefile:376: .depend: No such file or directory
Generating dependencies... 
/bin/sh: g++: not found
make: *** [.depend] Error 127
jordan@Jordan-Ubuntu:~/Desktop/Kismet/kismet-2007-10-R1$ make
g++  -O2 -Wall -DVERSION_MAJOR=\"2007\" -DVERSION_MINOR=\"10\" -DVERSION_TINY=\"R1\" -DTIMESTAMP=\"`cat TIMESTAMP`\"  -c util.cc -o util.o 
/bin/sh: g++: not found
make: *** [util.o] Error 127


I did however continue to type make install and install, but I got the same errors. If anyone can help me, I'm more than willing to learn and sitting patiently(while at work) waiting for replies.  
Thanks :)

---

### Post by Inxsible on 2007-11-29
I am not sure if this is correct since I never used Kismet. But the first thing to do whenever a package is missing is to go to Synaptic and search for it and install it.

System>>Administration>>Synaptic Package Manager

---

### Post by quandary on 2007-11-29
> **JO68 said:**
> Long story short, I'm an ultra noob, I've had Ubuntu 7.10 on my laptop for all of 3 days and it is my first time using anything other than Windows. I'm trying to install and get Kismet running (school project, trying to crack WEP) but i need to first get g++ working.  I have a friend in another country who was helping me a bit today but he had to get to bed.  So we got to a point where it seemed as if I would be able to install Kismet but then:

*** WARNING ***
LibPCAP was not found.  Kismet previously included a local copy of this
library, however it now expects libpcap to be provided by the system.
Kismet on Linux without LibPcap cannot capture data locally and will 
almost certainly NOT BE WHAT YOU WANT.
Your distribution should provide packages for libpcap, otherwise 
it can be downloaded from [http://tcpdump.org](http://tcpdump.org)

Configuration complete.  Run 'make dep' to generate dependencies
and 'make' followed by 'make install' to compile and install.
jordan@Jordan-Ubuntu:~/Desktop/Kismet/kismet-2007-10-R1$ make dep
Makefile:376: .depend: No such file or directory
Generating dependencies... 
/bin/sh: g++: not found
make: *** [.depend] Error 127
jordan@Jordan-Ubuntu:~/Desktop/Kismet/kismet-2007-10-R1$ make
g++  -O2 -Wall -DVERSION_MAJOR=\"2007\" -DVERSION_MINOR=\"10\" -DVERSION_TINY=\"R1\" -DTIMESTAMP=\"`cat TIMESTAMP`\"  -c util.cc -o util.o 
/bin/sh: g++: not found
make: *** [util.o] Error 127


I did however continue to type make install and install, but I got the same errors. If anyone can help me, I'm more than willing to learn and sitting patiently(while at work) waiting for replies.  
Thanks :)

> 
g++: not found

Looks like you didn't install g++.
Go to console and type: 
apt-get install g++

> 
...LibPCAP was not found.  ...
libpcap...can be downloaded from [http://tcpdump.org](http://tcpdump.org)

Do what it says.

If you miss a header-file you can do the following (at console):
apt-get update
apt-get install apt-file
then:
apt-file update
then:
apt-file search libpcap

PS: Kismet is slow. Use it only to sniff packets and save them. Then use aircrack

---

### Post by JO68 on 2007-11-29
Ive been to the Synaptic Package Manager a few times. Here is a screenshot of what I have installed when I do a search for g++

---

### Post by HokeyFry on 2007-11-29
you have to install the build-essential package. go to a terminal and type

sudo apt-get install build-essential

---

### Post by JO68 on 2007-11-29
Well its working somewhat, the make ran for a while and when I typed "make install" i got a few errors

jordan@Jordan-Ubuntu:~/Desktop/Kismet/kismet-2007-10-R1$ make install
make -e commoninstall
make[1]: Entering directory `/home/jordan/Desktop/Kismet/kismet-2007-10-R1'
mkdir -p /usr/local/etc
mkdir -p /usr/local/bin
install -o "root" -g "root" -m 755 kismet /usr/local/bin/kismet
install: cannot create regular file `/usr/local/bin/kismet': Permission denied
make[1]: *** [commoninstall] Error 1
make[1]: Leaving directory `/home/jordan/Desktop/Kismet/kismet-2007-10-R1'
make: *** [install] Error 2

Not exactly sure but I'm guessing I should specify where to be install it?

---

### Post by Inxsible on 2007-11-29
The permission denied error, usually means that you need to be root to be able to do that. Use a sudo before the command and try again.

---

### Post by JO68 on 2007-11-29
>  you have to install the build-essential package. go to a terminal and type

sudo apt-get install build-essential 


jordan@Jordan-Ubuntu:~$ sudo apt-get install build essential
[sudo] password for jordan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build
jordan@Jordan-Ubuntu:~$ jordan@Jordan-Ubuntu:~$ sudo apt-get install build essential
[sudo] password for jordan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build
jordan@Jordan-Ubuntu:~$ 


I'm full of Errors today!

---

### Post by Inxsible on 2007-11-29
> **JO68 said:**
> >  you have to install the build-essential package. go to a terminal and type

sudo apt-get install build-essential 


jordan@Jordan-Ubuntu:~$ sudo apt-get install build essential
[sudo] password for jordan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build
jordan@Jordan-Ubuntu:~$ 

I'm full of Errors today!That's build-essential, NOT build essential.

---

### Post by JO68 on 2007-11-29
build essential is done... damn you guys are good :)

---

### Post by JO68 on 2007-11-29
Kismet is installed Thank you all. Now I've got to read the readme for it and try to learn it sometime in the next few days. Thank you all, I'm so stoked about playing with this!

---

