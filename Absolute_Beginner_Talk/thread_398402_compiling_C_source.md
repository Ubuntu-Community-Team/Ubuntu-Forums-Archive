---
title: "compiling C source"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by colsandurz on 2007-04-01
I'm new to linux and trying to learn C.  So far, I've written a C program or two in Anjuta but it just saves it as an ordinary text file.  I thought C source files had a *.c extension... But if this is right, I still don't quite understand how to compile and then run the program.   And also, is compiling the C programs I write and compiling C source that I get from the Internet done in the same way?

would the run program be
```
./program_name
```

Thanks

---

### Post by taurus on 2007-04-01
You first need to install build-essential package before you can compile any C program.

```
sudo aptitude update
sudo aptitude install build-essential
```
Then, you can compile and run it with

```
gcc -o filename filename.c
./filename
```

---

### Post by SOULRiDER on 2007-04-01
First you need a C compiler, you should install the build-essential package first. To compile just do gcc <program source> and to run it ./<program_name>

As for stuff you download, you should have the checkinstall package installed so you can easily make .deb files. Also, all sources you download usually come with a readme file that explains how to compile them, but its ususally ./configure, then make and finaly sudo checkinstall.

---

### Post by colsandurz on 2007-04-01
I tried to compile a "hello world" program I found(so I knew the code was correct) but whenever I try to compile it I get an error.

```
#include <stdio.h>

main()
{
  for(;;)
      { 
          printf ("Hello World!\n");
      }
}

```

```
devin@dkelly:~$ gcc -o helloworld test.c
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status

```

---

### Post by jmarcos on 2008-03-11
I have  the same problem !!! Maybe there is something wrong with my open mpi lib ... Do anyone have a clue about what is going on?

---

### Post by Teber on 2008-03-11
[QUOTE=colsandurz;2384522]I tried to compile a "hello world" program I found(so I knew the code was correct) but whenever I try to compile it I get an error.

```
#include <stdio.h>

main()
{
  for(;;)
      } 
          printf ("Hello World!\n");
      {
}

```

this might work somewhat better. you closed main() with "{" instead of "}" and opened the second part with the closing "}"

---

### Post by Teber on 2008-03-11
looked it up in c manual of kernighan and ritchie:

```


#include <stdio.h>

main()
{
     printf("hello world\n");
}


```

hope this will compile

---

