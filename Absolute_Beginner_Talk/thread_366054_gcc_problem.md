---
title: "gcc problem"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by the.unclean.cpp on 2007-02-20
Hello. First of all I wanna say that I am an absolute beginner in Linux. I just installed Ubuntu Edgy and until now everything is going fine. I want to use Linux to learn programming. I wrote a program in C++, a simple one that produces a text: "Hello, Linux World!":
```
#include <iostream>
using namespace std;
int main()
{
   cout<<"Hello, Linux World!\n";
   return 0;
}
```
I compiled it with the following command:
```
gcc -o Hello Hello.cpp
```
and the terminal produced the following error:
```
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
```
I have the last version of gcc and my system is up to date.
What could be the problem?
Thanks in advance.

---

### Post by jvc26 on 2007-02-20
Have you installed the build-essential package?
If so I use the command:
```

g++ -o hello hello.cpp

```
to compile it

--Note this would be better in the programming talk section ;))
Il

---

### Post by taurus on 2007-02-20
Maybe try this first before you compile your program again.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by the.unclean.cpp on 2007-02-20
Thanks guys, the build-essential solved the problem.

---

