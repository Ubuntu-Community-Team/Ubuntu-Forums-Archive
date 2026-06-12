---
title: "C/C++ Not working"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by EricDallal on 2007-01-05
I wrote a simple "Hello World" program in C++ and it doesn't work. Nor does it work in C. Essentially, the gcc compiler can't find the header files:

Hello World.c:1:19: error: stdio.h: No such file or directory
Hello World.c:2:19: error: ctype.h: No such file or directory
Hello World.c:3:20: error: stdlib.h: No such file or directory
Hello World.c: In function ‘main’:
Hello World.c:6: warning: incompatible implicit declaration of built-in function ‘printf’

In case any of you are wondering if I'm just incompetent, here is the code:

#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>

int main() {
	printf("Hello World\n");
	return 0;
}

Has something gone wrong with the Ubuntu installation, do I have to point out the location of the header files, or do I need to install additional packages?

---

### Post by adwait on 2007-01-05
Apparently, it can't fine the library files that are to be included. Have you installed the build-essential package?

---

### Post by EricDallal on 2007-01-05
Probably not. Where can I find this package? I might have just missed it, but I thought I had gone through all the packages in the programming category and found none about C or C++ libraries.

---

### Post by Efwis on 2007-01-05
open terminal and type or copy and paste 
```
sudo aptitude install build-essential
```
this will install it and all of it's dependancies, should you decide to get rid of build-essential, which I doubt you will with doing programming, just type the following
```
sudo aptitude remove build-essential
```
This will remove it and all of it's dependancies that won't be used anymore.

---

### Post by EricDallal on 2007-01-05
Thanks. Actually I had just googled build-essential and found exactly the same thing. The installation worked and the program compiles fine now.

---

### Post by rickr765 on 2007-01-15
From an end-user standpoint, this is crap. I installed all the programming applications from the Add/Remove Applications dialog and did not get a working compile environment. Is anyone out there listening? This should be fixed ASAP.

---

### Post by rickr765 on 2007-01-15
Additionally, the sudo command above does not work.  Here are the error messages:

rick@number5:~$ sudo aptitude install build-essential
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rick@number5:~$

Remember that the standard installation does not specify any root user password, so I put my own user password in there.

---

### Post by NoWhereMan on 2007-01-15
> **rickr765 said:**
> Additionally, the sudo command above does not work.  Here are the error messages:

rick@number5:~$ sudo aptitude install build-essential
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

you can't run aptitude while you're running other package managers :D
close synaptic or gnome-app-install if they're open and give again the command ;)

---

### Post by zerhacke on 2007-01-15
I wonder why Ubuntu doesn't include gcc and all the stuff in build-essential by default?

---

### Post by rickr765 on 2007-01-15
NowhereMan, you the man! worked great.

And yes, zerhacke, they should definitely include it by default - at the very least, it should be in the Applications Install & Remove menu.

---

