---
title: "can't compile C packages in Ubuntu (help)"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by vitocool on 2007-09-23
Ok, I just set up my laptop with dual boot.  Using Ubuntu 7.04.  My problem is this....  I am in the process of installing NS-2 (the network simulator) for my networks class.  I have downloaded and untarred the NS-2 package.  The problem is, when I run the install executable in the NS-2 package, it needs to compile a bunch of C files and cannot because it cannot locate the C packages and gcc.  I see that the packages came with Ubuntu, but how do I set up my system to be able to run gcc?  Please help as soon as possible.

---

### Post by cheetaux on 2007-09-23
Try the following:

sudo apt-get install gcc

sudo apt-get install build-essential

---

### Post by Frak on 2007-09-23
In the terminal copy and paste this
```
sudo aptitude install build-essential
```

And try again.

---

### Post by vitocool on 2007-09-23
actually, gcc is supposedly on my ubuntu system because when I type gcc at the terminal prompt, it says this...

[B] gcc: no input files
[/B]

also, this is the portion of the output having to do with gcc when I try to run the install of NS-2...

[B]checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
[/B]

Can someone tell me what I need to do?

---

### Post by cheetaux on 2007-09-23
(1) Did you do?

> sudo apt-get install build-essential 

(2) Have you tried compiling a simple C program as the following

> #include <stdio.h>
int main() {
   printf("Hello World\n");
}

Save the above in a file called hello.c

Then execute

>  gcc hello.c -o hello

This this create an executable called hello

---

### Post by EchoBeach on 2007-09-23
i vitocool
Does 'Add/Remove Programs' show gcc as installed?
What response do you get when you try the following in a terminal?

sudo apt-get install gcc
sudo apt-get install build-essential

Regards
Echo

---

### Post by vitocool on 2007-09-23
frak i executed the code you said, and this is what happened:

[B]victor@victor-laptop:~/Desktop/NS-2/ns-allinone-2.31$ sudo aptitude install build-essential
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
[/B]

then, I ran it again because of the above message saying it could not get a lock (I closed all applications first) and this is what it spit out....

[B]victor@victor-laptop:~/Desktop/NS-2/ns-allinone-2.31$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "build-essential"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[/B]

then I tried to install the NS-2 simulator package and it did not work.  It's not finding gcc here is the beginning of the output from trying to do this...

[B]victor@victor-laptop:~/Desktop/NS-2/ns-allinone-2.31$ ./install
============================================================
* Testing for Darwin (OS X) environment
============================================================
============================================================
* Testing for Cygwin environment
============================================================
Cygwin not detected, proceeding with regular install.
============================================================
* Build XGraph-12.1
============================================================
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking if malloc debugging is wanted... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
make: *** No targets specified and no makefile found.  Stop.
Can not create xgraph; But xgraph is an optional package, continuing...
============================================================
[/B]

---

### Post by vitocool on 2007-09-23
Echo, no gcc is not in the list of add/remove programs.  very good question.

---

### Post by Maestro23 on 2007-09-23
Vitocool, do you have all your repositories enabled (universe, mutliverse, etc..)?

Because you should have found "build-essential".

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

---

### Post by vitocool on 2007-09-23
echo, here is the output of the first command u asked about....

[I]victor@victor-laptop:~/Desktop/NS-2/ns-allinone-2.31$ sudo apt-get install gcc
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 115 not upgraded.
[/I]

as for the second command, i believe it worked.  it asked for password and began installing various packages while requiring an additional 33 MB of space.  I will try to compile a simple C program as you suggested.  I will let u know what happens.  Thanks for your lightning fast help!

---

### Post by cheetaux on 2007-09-23
Please do the following:

(1)
> sudo apt-get install gcc
sudo apt-get install build-essential

(2) Create the following C program and save it in a file called hello.c

> #include <stdio.h>
int main() {
printf("Hello World\n");
}


Then execute

> gcc hello.c -o hello

Let me know what happens.

---

### Post by vitocool on 2007-09-23
echo, gcc works now, at least for the hello world simple app.  Problem is, after I ran the install executable for NS-2, there seemed to be a bunch of warnings and erros and what not in the output.    

In particular I am getting a lot of "Invalid type" errors in the output.  Mainly, it is referring to symbols and functions such as the arrow symbol (->) which is used in C.  Any suggestions?

---

### Post by cheetaux on 2007-09-23
Can you copy/paste some of the warnings/error messages you are getting?

If they are just warnings, you can probably ignore them.

---

### Post by EchoBeach on 2007-09-23
Cheetaux
I have gcc in my 'Add/Remove...'.  I tried your small example and the gcc command returned no messages, but there is now a 'hello' file present.
Dumb question!:
How do I invoke this new file - to make sure it works?
Echo

---

### Post by vitocool on 2007-09-23
here are just some of the errors...


[I]/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1308: error: ‘TkBorder’ has no member named ‘colormap’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1311: error: ‘TkBorder’ has no member named ‘objRefCount’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘TkDebugBorder’:
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1391: error: ‘TkWindow’ has no member named ‘dispPtr’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1394: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1394: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1400: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1403: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1405: error: ‘TkBorder’ has no member named ‘objRefCount’
make: *** [tk3d.o] Error 1
tk8.4.14 make failed! Exiting ...
For problems with Tcl/Tk see [http://www.scriptics.com](http://www.scriptics.com)
[/I]

---

### Post by vitocool on 2007-09-23
here are some other errors when trying to install NS-2....

[I]/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1138: error: invalid type argument of ‘unary *’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1138: error: invalid type argument of ‘unary *’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1139: error: invalid type argument of ‘->’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1139: error: invalid type argument of ‘->’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1140: error: invalid type argument of ‘->’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1140: error: invalid type argument of ‘->’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1158: error: invalid type argument of ‘->’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1164: error: invalid type argument of ‘->’
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: At top level:
/home/victor/Desktop/NS-2/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1189: error: static declaration of ‘Intersect’ follows non-static declaration
[/I]

---

### Post by EchoBeach on 2007-09-23
vitocool
Could your NS-2 have other dependencies that it can't find?
Echo

---

### Post by vitocool on 2007-09-23
it appears as though I have it.  I used this page as a reference... [http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04](http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04)

let's hope everything installed ok

---

