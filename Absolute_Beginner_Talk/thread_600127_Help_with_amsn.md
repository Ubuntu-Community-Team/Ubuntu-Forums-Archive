---
title: "Help with amsn"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by shimmy66 on 2007-11-01
Hi, I am brand new to linux and im not really 100% sure what im doing  so sorry if this is a silly question. I have been trying to install aMSN  but I keep getting the error message

Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 7.10 (apt-get) to install a package with similar name to 'tcl'. 

Error: Unable to prepare package AMSN MSN client.

any help would be greatly appreciated.
Thank you

---

### Post by jusmurph on 2007-11-01
Try installing pidgin, it will happily work with msn interchanges (amongst many others).

In Terminal:
```
sudo apt-get install pidgin
```

---

### Post by ozylog on 2007-11-01
do u ever try using add/remove (applications > add/remove), then searching "amsn". click checkbox and apply....??

do you have repository cds?do u have internet connection??


or you can do it with automatix2: [http://www.getautomatix.com/](http://www.getautomatix.com/)

download automatix2(.deb) for gutsy and double click it..

install and u can enjoy all of programs there include amsn....

---

### Post by Maestro23 on 2007-11-01
> **shimmy66 said:**
> Hi, I am brand new to linux and im not really 100% sure what im doing  so sorry if this is a silly question. I have been trying to install aMSN  but I keep getting the error message

Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 7.10 (apt-get) to install a package with similar name to 'tcl'. 

Error: Unable to prepare package AMSN MSN client.

any help would be greatly appreciated.
Thank you

Do you have a link to the download?

---

### Post by MrFSL on 2007-11-02
open a terminal and type the following:

```
sudo apt-get install amsn
```

Enter your password and it should install.

---

### Post by xonegon on 2008-06-14
> **MrFSL said:**
> open a terminal and type the following:

```
sudo apt-get install amsn
```

Enter your password and it should install.


And if you are a total noob as me, don't forget to first
```
cd /home/username/downloaddirectory

```

---

