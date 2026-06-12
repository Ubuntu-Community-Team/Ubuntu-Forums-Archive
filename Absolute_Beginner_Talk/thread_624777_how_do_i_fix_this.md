---
title: "how do i fix this"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by leedsdevil on 2007-11-27
ok i installed a new hd in the wifes pc but know i can install anything other than what was already installed
file:///home/g/Desktop/Link%20to%20Screenshot-synaptic.png
i hope this link works but if it does not ill type out what it says
e:dpkg was interrupted, you must manually run dpkg -- configure -a to correct the problem
please easy instructions so i can keep the wife off my back lol thx all who help

---

### Post by Paul820 on 2007-11-27
Open the terminal and type
> sudo dpkg -- configure -a

---

### Post by skyjacker on 2007-11-27
> **leedsdevil said:**
> ok i installed a new hd in the wifes pc but know i can install anything other than what was already installed
file:///home/g/Desktop/Link%20to%20Screenshot-synaptic.png
i hope this link works but if it does not ill type out what it says
e:dpkg was interrupted, you must manually run dpkg -- configure -a to correct the problem
please easy instructions so i can keep the wife off my back lol thx all who help
```
sudo dpkg -- configure -a
``` Good Luck!:)

---

### Post by leedsdevil on 2007-11-27
thanks for the fast response im still stuck it wants options any help?

---

### Post by leedsdevil on 2007-11-27
g@g-desktop:~$ sudo dpkg -- configure -a
[sudo] password for g:
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
g@g-desktop:~$ sudo dpkg -- configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
g@g-desktop:~$

---

### Post by taurus on 2007-11-27
```
sudo dpkg **--configure** -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by leedsdevil on 2007-11-27
we are getting thereHit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Fetched 3B in 0s (4B/s)  
Reading package lists... Done
g@g-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
g@g-desktop:~$

---

### Post by taurus on 2007-11-27
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by leedsdevil on 2007-11-27
&#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                     i can hit the ok

---

### Post by meborc on 2007-11-27
this is just the licence agreement... so read it... then select ok by TAB key... and enter

---

### Post by leedsdevil on 2007-11-27
Thanks that did it

---

