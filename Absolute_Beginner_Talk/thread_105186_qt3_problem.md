---
title: "qt3 problem"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-12-17
when i try to compile a program using g++ i get this error:

:~/Desktop$ g++ hello.cpp
hello.cpp:1:26: error: qapplication.h: No such file or directory
hello.cpp:2:20: error: qlabel.h: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:6: error: ‘QApplication’ was not declared in this scope
hello.cpp:6: error: expected `;' before ‘ap’
hello.cpp:7: error: ‘QLabel’ was not declared in this scope
hello.cpp:7: error: ‘label’ was not declared in this scope
hello.cpp:7: error: expected type-specifier before ‘QLabel’
hello.cpp:7: error: expected `;' before ‘QLabel’
hello.cpp:8: error: ‘app’ was not declared in this scope

i got the program out of a book, so it should be correct.
does anyone know how to change the path on linux to point 
to the right location.
i also installed qt3 using: sudo apt-get install qt3-dev-tools.
i would really appreciate any help that i can get

---

### Post by GoldBuggie on 2005-12-17
```
sudo apt-get libqt3-mt-dev
```

---

### Post by grim918 on 2005-12-18
thank you i will try at as soon as i get home. by the way do you know if there are any flags that i should include when compiling.

---

### Post by grim918 on 2005-12-18
ok i used: sudo apt-get install libqt3-mt-dev
it installed everything without any problems but im still getting the 
same errors as above. do you know how to change the path.
im think i need to tell the compiler where to look for the files, but im
new to linux and im not used to the file system yet. do you know where 
linux stores the qt3 header files. i tried using locate but had no results

---

### Post by GoldBuggie on 2005-12-18
Ahh...sorry for not pointing that out int the beginning since ofcourse the program needs to know where the headerfiles are. There might be some flag for g++ that tells the compiler t include that directory and look for headers there but as I can't remember such a flag at the moment and i'm sitting at work i'll tell you the other way(please look at the g++ manual for the other way if you can, i'll maybe look into this later). 

When you do the **#include "qt...."** include the directory; 
**#include "/usr/......file.h"**

To find out there they are you can do a **dpkg -L libqt3-headers** <--- this package was included in the -dev package. You can look at specific info for packages by **apt-cache show libqt3-mt-dev**. Anyway the directory for qt3-headers is **/usr/include/qt3/**.

Sorry if i wrote to much I just wanted to give you some info so that  you might use in the future. 

PS. If you want to know more about *dpkg* or *apt-cache* do a *man dpkg *or *man apt-cache*

Hope this helps.

---

### Post by GoldBuggie on 2005-12-18
ok i had nothing to do today...hehe..j/k

I looked it up...If you use the regular #include <qt3.h> then gcc will look in the following directories. 
[I]      /usr/local/include
      /usr/lib/gcc-lib/target/version/include
      /usr/target/include
      /usr/include 

[/I] If you want to include a directory use the -Idir
So just do a **g++ -I/usr/include/qt3 hello.cpp**

---

### Post by grim918 on 2005-12-19
ok i got it working now. thank you very much for taking the time to help me out. now its time for me to finally teach myself some C++ GUI programming.

---

