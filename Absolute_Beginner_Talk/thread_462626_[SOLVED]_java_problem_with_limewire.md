---
title: "[SOLVED] java problem with limewire"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-06-02
ok, 2 days ago my limewire was working perfectly, today however it says i need to upgrade my java to 1.4.x or the newer version, so i i ran the command java -version and it says i have version 1.4.2

any ideas?
here is what i have exactly.
```
k33bz@treehouse:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
k33bz@treehouse:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
k33bz@treehouse:~$ 

```

---

### Post by taurus on 2007-06-02
You need the Sun's java.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```

---

### Post by k33bz on 2007-06-02
that didnt work, i still get the exact same thing

---

### Post by taurus on 2007-06-02
Did you get any error message when you ran those commands from a terminal?  And I suppose you are running Feisty.

---

### Post by k33bz on 2007-06-02
ya im using Feisty, and i didnt receive any error commands while running those commands, still says i have the dame version, and limewire still having the same response

---

### Post by taurus on 2007-06-02
Can you post the complete output of these two commands from a terminal?

```
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by k33bz on 2007-06-02
par 1
```
k33bz@treehouse:~$ sudo aptitude update
Get:1 http://archive.ubuntustudio.org feisty Release.gpg [189B]
Ign http://archive.ubuntustudio.org feisty/main Translation-en_US               
Hit http://archive.ubuntustudio.org feisty Release                              
Hit http://archive.ubuntustudio.org feisty/main Packages                        
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]  
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Get:3 http://medibuntu.sos-sts.com feisty Release.gpg [189B]         
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US       
Get:4 http://us.archive.ubuntu.com feisty Release.gpg [191B]         
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US 
Hit http://medibuntu.sos-sts.com feisty Release                      
Get:5 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B] 
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security/main Packages       
Get:6 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Hit http://medibuntu.sos-sts.com feisty/free Packages                
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/restricted Packages              
Hit http://security.ubuntu.com feisty-security/main Sources          
Hit http://security.ubuntu.com feisty-security/restricted Sources    
Hit http://us.archive.ubuntu.com feisty-updates Release              
Hit http://us.archive.ubuntu.com feisty-backports Release                       
Hit http://medibuntu.sos-sts.com feisty/non-free Packages                       
Hit http://medibuntu.sos-sts.com feisty/free Sources                            
Hit http://medibuntu.sos-sts.com feisty/non-free Sources                        
Hit http://security.ubuntu.com feisty-security/universe Packages                
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Fetched 6B in 1s (4B/s)  
Reading package lists... Done

```

---

### Post by k33bz on 2007-06-02
part 2

```
k33bz@treehouse:~$ sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

---

### Post by taurus on 2007-06-02
How about

```
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-fonts
```

---

### Post by k33bz on 2007-06-02
same thing

```
k33bz@treehouse:~$ sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

---

### Post by k33bz on 2007-06-02
would i be able to fix it if i just unistall java then reinstall it??

if so how do i unistall java?

---

### Post by taurus on 2007-06-02
I think it's time to have a look at your repos.  Post

```
cat /etc/apt/sources.list
```

---

### Post by k33bz on 2007-06-02
```
k33bz@treehouse:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
k33bz@treehouse:~$ 

```

---

### Post by taurus on 2007-06-02
Can you open synaptic, System -> Administration -> Synaptic Package Manager, and Search for java?  Do you see anything on the list?

---

### Post by k33bz on 2007-06-02
> **taurus said:**
> Can you open synaptic, System -> Administration -> Synaptic Package Manager, and Search for java?  Do you see anything on the list?

wow, it is there, but it says it is not installed, im installing it right now, let ya know what happens

---

### Post by taurus on 2007-06-02
Once it's done, close synaptic and run this command from a terminal to see which version you are using now.

```
java -version
```

---

### Post by k33bz on 2007-06-02
it works now, and it says this

```
k33bz@treehouse:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
k33bz@treehouse:~$ 

```

how or why did it remove itself to begin with, kuz as i said it was working fine just 2 dats ago?

---

### Post by k33bz on 2007-06-02
o, and how do i change the limewire icon from a plug to the one i am familiar with, i have done it before from a post i had seen somewhere else for a freinds computer for edgy, but i cant find it no more, PS im using Feisty

---

