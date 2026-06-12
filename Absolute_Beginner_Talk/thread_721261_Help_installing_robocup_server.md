---
title: "Help installing robocup server"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by loizos13 on 2008-03-11
I am trying to install the robocup server on ubuntu gutsy 7.10 but i keep getting error messages when i am trying to use 'make' in the base code. If anyone knows the necessary  programs i shall install before installing the server it would be helpful..

---

### Post by seakage2h on 2008-04-23
Hello, loizos13

I've just finished installing the three components of robocup server: **rcssbase**, **rcssserver** and **rcssmonitor.** I've also met some error messages while compiling rcssbase. Fortunately I've figured it out. Let me list the details below:

[LIST]
[*]You may have encounterd the make error messages saying that boost/filesystem/path.hpp, boost/filesystem/operations.hpp not exist or so. The reason is that robocup server heavily depends on the **Boost C++ library**, but ubuntu only installed several of libboost-* by default(I haven't figured out why configure didn't check it over). So use apt-get to install all libboost-* packages(May not all are neccesary, but I didn't check it in detail).
```
sudo apt-get install libboost-*
```
[*]While making install rcssbase, it reports that some robocup libraries are installed and provides the path. The libraries will be linked when compile rcssserver, so we should make it linkable. Just add the path to **/etc/ld.so.conf**, or elegantly make it a single file named robocup.conf and put it in **/etc/ld.so.conf.d/**. Later on the path reported by rcssserver should also be added. In my situation, I added
```
/home/robocup/lib
/home/robocup/lib/rcssserver/modules
```
in **/etc/ld.so.conf.d/robocup.conf**


[*]rcssmonitor require **libxpm**, install the development package if not available. These likes of dependency problems are successfully reported by configure, just pay attention to it.
[/LIST]

---

### Post by dabbelju on 2008-05-21
Hi,

I try to install the robocup Srever version 12.1.0 ob my ubuntu 8.04.

It did not work. I install all libboost-* Packages, but "make" makes trouble.

Pastes:
./configure --prefix=$RCSSBASEDIR : [http://ubuntuusers.de/paste/219598/](http://ubuntuusers.de/paste/219598/)
make : [http://ubuntuusers.de/paste/219597/](http://ubuntuusers.de/paste/219597/)

It looks that my libboost-version 1.34.1 is not compatiple with te version 12 of rcss-base

Any idea, what I can do?

Greetings
Robert

---

### Post by seakage2h on 2008-07-11
Hello, Robert

Actually I was also using ubuntu 8.04 and libboost 1.34.1 to build rcssbase and other components of rcssserver. 

I've checked your configure output and the make output. No obvious problem in your configure output is found. Then I run configure in my own system once again and compared with that of yours----but merely no difference.

Your set the make output in german which I can't understand, but I guess the main problem is said on line 30:
/home/dabbelju/local/include/boost/config/compiler/gcc.hpp:66:7: Warnung: #warning "Unknown compiler version - please run the configure tests and report the results" 

I compile the rcssserver with gcc 4.3, maybe you can try to switch gcc to a newer one. Wish you succeed!

Best regards.

---

