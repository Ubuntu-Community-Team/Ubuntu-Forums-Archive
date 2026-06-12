---
title: "c++ compiler + bgi"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by LinuxIsInnovation on 2007-12-18
Hello, 
Is there a GNU C++ Compiler that supports BGI Graphics and console I/O??

---

### Post by nowshining on 2007-12-18
have u looked at all the c ++ compilers in the synaptic package manager

---

### Post by LinuxIsInnovation on 2007-12-18
I have used gcc, g++, anjuta...
Gcc and g++ donot support bgi graphics and/or console I/O
Anjuta is more like a mere GNU editor with no option to Compile/Build..

---

### Post by nowshining on 2007-12-18
well then sorry that's all i know :( i hope u find what u need soon. :)

---

### Post by LaRoza on 2007-12-18
BGI was used by Borland, in the days of DOS. It is not portable and is not maintained.

What do you mean by "Console I/O"? You can use NCurses, or the standard library for IO operatings.

---

### Post by LinuxIsInnovation on 2007-12-19
I need BGI Graphics for project purposes.
COnsole I/O includes getch, putch operations. These operations are one key operations and they are quite useful in many cases. Is there any graphics alternative I can use in Linux. My minimum requirement for a graphics environt is as low as 4-bit color at 640x480 resolution. Please suggested any related graphics solution.

---

### Post by LaRoza on 2007-12-19
> **sayakb said:**
> I need BGI Graphics for project purposes.
COnsole I/O includes getch, putch operations. These operations are one key operations and they are quite useful in many cases. Is there any graphics alternative I can use in Linux. My minimum requirement for a graphics environt is as low as 4-bit color at 640x480 resolution. Please suggested any related graphics solution.

getch is in conio.h, a Windows specific header, and not part of Ansii C, you can use ncurses, see [http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific).

Ncurses has a function names "getch" and it behaves the same way (AFAIK).

---

### Post by LinuxIsInnovation on 2007-12-19
Heres a basic HelloWorld code:

//Test.cxx
#include<curses.h>
#include<iostream.h>

int main(void)
{
   cout<<"HelloWorld;
   getch();
   return 0;
}


Heres the output I get:

glade@Muzic-Jukebox:~$ gcc test.cxx
In file included from /usr/include/c++/4.1.3/backward/iostream.h:31,
                 from test.cxx:2:
/usr/include/c++/4.1.3/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
test.cxx: In function &#8216;int main()&#8217;:
test.cxx:8: error: return-statement with no value, in function returning &#8216;int&#8217;
glade@Muzic-Jukebox:~$ 

I'm a linux newbie, please don't mind if there is a stupid mistake in this :D
Just point it out for me.. :)

---

### Post by LaRoza on 2007-12-19
There are many problems with that program.

There errors you have are the result of not using <iostream> (don't use .h), and using the wrong header, it is <ncurses.h>. You must link to it when you compile with the -lncurses flag.

Install ncurses with:

```

sudo aptitude install libncurses5-dev

```

Use the ncurses tutorials at [http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific)

---

### Post by LinuxIsInnovation on 2007-12-20
glade@Muzic-Jukebox:~$ sudo aptitude install libncurses5-dev
Scan right index finger on AuthenTec AES2501

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  devhelp-common fuseiso libgbf-1-common 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2163kB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
glade@Muzic-Jukebox:~$ 

Can I remove these packages?

---

### Post by LinuxIsInnovation on 2007-12-20
It says its unused but fuse is used for NTFS writing I think

---

### Post by LaRoza on 2007-12-20
> **sayakb said:**
> glade@Muzic-Jukebox:~$ sudo aptitude install libncurses5-dev
Scan right index finger on AuthenTec AES2501

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  devhelp-common fuseiso libgbf-1-common 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2163kB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
glade@Muzic-Jukebox:~$ 

Can I remove these packages?

```

sudo aptitude remove devhelp-common fuseiso libgbf-1-common 

```

---

### Post by LaRoza on 2007-12-20
> **sayakb said:**
> It says its unused but fuse is used for NTFS writing I think
```

FUSE module to mount ISO filesystem images
This package provides a module to mount ISO filesystem images
using FUSE.
With FUSE it is possible to implement a fully functional
filesystem in a userspace program.

It can also mount single-tracks .BIN, .MDF, .IMG and .NRG.

 Homepage: http://fuse.sourceforge.net/wiki/index.php/FuseIso

```

From Synaptic

---

