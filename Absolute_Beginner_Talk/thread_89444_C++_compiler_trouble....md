---
title: "C++ compiler trouble..."
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-11-12
i tried to run gcc or g++ from the command prompt and the commands were not recognized so i ran sudo apt-get install g++. the installation went ok but when i try to compile any programs i get errors even when trying to compile the easiest of programs such as the hello world. i was wondering if there are libraries that i must also include. or if ubuntu comes with a compiler and i was just doing something wrong at the command prompt. id appreciate any help that i can get

---

### Post by apjone on 2005-11-12
use synaptic and seach for it in description and name

gtk++ c+ c++ c etc

---

### Post by DJ_Max on 2005-11-12
[http://help.ubuntu.com/starterguide/C/ch03s08.html#id2531297](http://help.ubuntu.com/starterguide/C/ch03s08.html#id2531297)

---

### Post by fara on 2005-11-12
let us know what you type on your command line and exactly what you get when you run it.

---

### Post by grim918 on 2005-11-12
this is what i type in. 

command line:gcc hello.c
grim918@ubuntu:~/C++$ gcc hello.c
hello.c:2:20: error: iostream: No such file or directory
hello.c: In function ‘main’:
hello.c:4: error: syntax error before ‘:’ token

i checked the file so the code is correct. it says that im missing a file and im wondering if i havet to download some libraries

---

### Post by dogen on 2005-11-12
OK, we know you're compiler can't find IOStream. Either it's not there or the compiler doesn't know where to look. I'm not at my home computer at the moment, so I can just give you general advice. Find out if IOStream is in your cpp lib directory. If not get it, (but I assume it's there), if yes, find out how the compiler knows where to look for its libraries. Probably a path setting of some sort, since your not using a make file. Google is your friend.

---

### Post by LHZ on 2005-11-12
The easiest way to get all the libraries and stuff for the gcc/g++ compiler is to open up a terminal and type 

> sudo apt-get install build-essential

You can also Synaptic for 'build-essential' if you prefer. 
Installing gcc/g++ *just* gives you the compiler and nothing else, build-essential gives you the full set of tools to work with (if I'm not mistaken, it also installs compilers/interpreters for a number of other laguafges).

---

### Post by grim918 on 2005-11-12
i tried to run the command:
:sudo apt-get install build-essential         

and i ended up with this error:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
E: Broken packages


do you know how i can fix this.

---

