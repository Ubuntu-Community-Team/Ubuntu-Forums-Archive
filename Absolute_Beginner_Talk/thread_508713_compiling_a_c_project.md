---
title: "compiling a c project"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-07-24
Hi
Simple question.
I am trying to compile the following c project in linux. My question is how to?
Thxs, Kris

#include <bios.h>

#include <conio.h>



#define COM1       0

#define DATA_READY 0x100

#define SETTINGS ( 0x80 | 0x02 | 0x00 | 0x00)



int main(void)

{



   int in, out, status;

   bioscom(0, SETTINGS, COM1); /*initialize the port*/

   cprintf("Data sent to you:  ");



   while (1)

   {



      status = bioscom(3, 0, COM1); /*wait until get a data*/

      if (status & DATA_READY)

           if ((out = bioscom(2, 0, COM1) & 0x7F) != 0)  /*input a data*/

              putch(out);



           if (kbhit())

           {

              if ((in = getch()) == 27)   /* ASCII of Esc*/

                 break;



              bioscom(1, in, COM1);   /*output a data*/

           }



   }



   return 0;



}

---

### Post by nitro_n2o on 2007-07-24
first you need to have build-essentials 
```
sudo apt-get install build-essentials 
```
then: 
```
gcc <filename.c> -o <outputfile> 
```
if you don't specify the -o flag , that is: gcc <fliename.c> only you'll get a.out as the output (compiled) file

---

### Post by LaRoza on 2007-07-24
It is
```

sudo aptitude install build-essential

```
No "s" in essential

Use gcc for C programs and g++ for C++ programs. Most of the time, C programs will compile fine with g++.

---

### Post by krisfrajer on 2007-07-24
What can I do with these missing libraries?
This is an error that I get when I try to compile. I think I have gcc already install... by the way, I am using fedora at work so build-essentials does not work... BUt I am sure gcc is already installed with the basic libraries. Thxs for the help.

bash-3.1$ gcc com1.c -o com1
com1.c:1:18: error: bios.h: No such file or directory
com1.c:3:19: error: conio.h: No such file or directory

---

### Post by kevdog on 2007-07-24
Try 
sudo aptitude install linux-headers-`uname -r`

Maybe that will work

---

### Post by asmoore82 on 2007-07-24
who or what told you to use those header files?

---

### Post by nitro_n2o on 2007-07-24
oops sorry for the extra 's' :oops: 
just wondering.. is that windows code?

---

### Post by krisfrajer on 2007-07-24
I borrowed this file from the web ;) . I am not sure about the bios header, but the conio header is a very standard. When I compile the files, do I have to include the header files too?
Kris

---

### Post by LaRoza on 2007-07-24
Although gcc is installed, it is missing everything, including the headers, including stdio.h.

Type
```

sudo aptitude install build-essential

```

And you will get everything you need for C/C++ programming.

You can install the headers seperately, but I don't recommend it.

-EDIT I didn't look at your code, so I don't know if it will compile on Linux.

---

### Post by krisfrajer on 2007-07-24
Now that you mention it, yes, that is windows code because of the definition of the com port. I think I have to use something like 'tssd05' or something about those lines to open com ports through linux. I got to read about that. 
There is my gcc version. 

bash-3.1$ gcc -v
Using built-in specs.
Target: i386-redhat-linux
Configured with: ../configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --enable-shared --enable-threads=posix --enable-checking=release --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-libgcj-multifile --enable-languages=c,c++,objc,obj-c++,java,fortran,ada --enable-java-awt=gtk --disable-dssi --enable-plugin --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-1.4.2.0/jre --with-cpu=generic --host=i386-redhat-linux
Thread model: posix
gcc version 4.1.2 20070626 (Red Hat 4.1.2-13)

---

### Post by jdackle on 2007-07-24
I remember a good while back ago I compiled a small program I'd written for DOS (to create a 0 bytes-long file) and it worked seemingly "out of the box"!!! I was like :confused: 
:lolflag:
But that was in Mandrake so... Some headers might be present in there and not in Ubuntu.. Dunno. :(

Anyways, it just crossed my mind that if you don't have the headers installed in your standard location, you may neeed to specify the full path in the .c file. E.g.:
```
#include </usr/local/include/dos/bios.h>
```

Just a thought...

---

### Post by Cypher on 2007-07-24
Wow..conio.h, that takes me back to my CS College days..that's a custom header file that was provided by a particular C-programming book author to baiscally hide the scary "scanf"-related functions. This is not a standard header and you really shouldn't use it. Use "stdio.h" instead of the standard "printf", "scanf", "getc" functions..

Secondly, that's a DOS program you are trying to play with. There is no "COM1" in Linux. You'd have to do someting like
```

fd = fopen("/dev/ttyS1", "w");

```
to open the COM1 port..

---

