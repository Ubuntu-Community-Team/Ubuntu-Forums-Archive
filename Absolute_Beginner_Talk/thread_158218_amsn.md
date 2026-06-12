---
title: "amsn"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Jonzo on 2006-04-10
Hi,

I'm trying to install amsn on Kubuntu 5.10 i386..
getting the following:

```

jonzo@ubuntu:~/amsn-0.95$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for prefix by checking for wish... /usr/bin/wish
checking tcl build dir... configure: error: Unable to find Tcl directory or Tcl package is not tcl-dev

```

I have build-essential, if that helps.  Thanks.

---

### Post by Swiss on 2006-04-10
Just use:

```
sudo apt-get install amsn
```


Thant should work right dandy...

---

### Post by Jonzo on 2006-04-10
Yeah, you're right - that will work.  But I want to know why I can't compile it myself.

Anyone?

---

### Post by Swiss on 2006-04-10
Try this: 

sudo apt-get install tcl8.4-dev

---

### Post by Jonzo on 2006-04-10
Got this:

```

jonzo@ubuntu:~/amsn-0.95$ sudo apt-get install tcl8.4
Reading package lists... Done
Building dependency tree... Done
tcl8.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

---

### Post by Jonzo on 2006-04-10
[QUOTE=Swiss]Just use: ```
sudo apt-get install amsn
``` Thant should work right dandy...[/QUOTE] Oh for the record... that doesn't work. :(

```

jonzo@ubuntu:~/amsn-0.95$ sudo apt-get install amsn
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package amsn
jonzo@ubuntu:~/amsn-0.95$   
```

---

### Post by Swiss on 2006-04-10
tcl8.4-dev

not:

tcl8.4
> 
jonzo@ubuntu:~/amsn-0.95$

You're still in cd.
try:

sudo apt-get update
sudo apt-get check
sudo apt-get build-dep amsn

---

### Post by mishranurag on 2006-04-10
For KDE, try kmess.

---

### Post by Swiss on 2006-04-10
If everything else fails you probably don't have the universe repo enabled.
Fix:

System>Administration>Synpatic Package Manager.
In Synaptic Goto: Stettings>Repositories>Add.

Then check the Comunity Maintained (Universe) and click OK.
Then sudo-you-know-what

---

