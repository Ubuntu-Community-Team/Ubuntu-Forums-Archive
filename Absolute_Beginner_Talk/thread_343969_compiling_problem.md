---
title: "compiling problem"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Elrohir on 2007-01-22
ok, so I have no idea how to compile a program using 'gcc'... I have a text file ('cprogram') with the 'Hello World' code... Then I go to Terminal and try to compile this way:```
gcc cprogram
```and I get this error:```
/usr/bin/ld:cprogram: file format not recognized; treating as a linker script
/usr/bin/ld:cprogram:1: syntax error
collect2: ld returned 1 exit status
``` :confused: anyone? help?

just in case you need it, here's the Hello World program:[FONT=Verdana]
[/FONT]```
[FONT=Verdana]#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}
[/FONT]
```

---

### Post by onsy on 2007-01-22
Hi, 
Try to rename your file cprogram.c and then type : 
cpp -o cprogram cprogram.c

---

### Post by Elrohir on 2007-01-22
we might be getting somewhere, but now I have new error messages:
```
cprogram.c:3:20: error: iostream: No such file or directory
cprogram.c:4: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'namespace'
cprogram.c: In function 'main':
cprogram.c:8: error: 'cout' undeclared (first use in this function)
cprogram.c:8: error: (Each undeclared identifier is reported only once
cprogram.c:8: error: for each function it appears in.)
``` if you ask me, I guess its not including the iostream header... if it is so, where do I find it?

---

### Post by Henry Rayker on 2007-01-22
iostream should be in /usr/include/c++/[version number...mine is 4.1.2]/

---

### Post by rocketman768 on 2007-01-22
This is a C++ program. The name should be cprogram.cpp

---

### Post by lamego on 2007-01-22
You need to read some tutorial like:
[http://www.arachnoid.com/cpptutor/setup_unix.html](http://www.arachnoid.com/cpptutor/setup_unix.html)

---

### Post by Elrohir on 2007-01-23
> **rocketman768 said:**
> This is a C++ program. The name should be cprogram.cpp
did this and no progress... .c was better...

[quote=lamego]You need to read some tutorial like:
[http://www.arachnoid.com/cpptutor/setup_unix.html](http://www.arachnoid.com/cpptutor/setup_unix.html)[/quote]
actually, I'm following this one: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by rocketman768 on 2007-01-27
The problem is that it's treating your c++ program as if it were a c program. I.e., it's not including the c++ library and that's why it says that iostream and cout are not defined. The reason I told you to rename it "whatever.cpp" is that usually gcc will see the .cpp and realize that it's supposed to be a c++ program and it will compile it with the c++ library junk.

However, the problem may lie in the fact that you do not have g++ installed. It is the _real_ compiler and c++ environment. So get it using aptitude or whatever package manager you like. Don't hold me to it, but I believe that

```
apt-get install g++
```

...will work. Instead of g++, it might be g++-3.3 or something like that.

---

