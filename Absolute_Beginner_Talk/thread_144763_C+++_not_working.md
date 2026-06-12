---
title: "C+++ not working"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by paradize on 2006-03-15
I'm trying to compile a very simple c++ program in ubuntu and its not compiling , giving some errors

I give g++ test.cc

errors shown ...
/usr/include/c++/4.0.2/cwchar: At global scope:
/usr/include/c++/4.0.2/cwchar:223: error: â::wcsstrâ has not been declared
/usr/include/c++/4.0.2/cwchar: In function âwchar_t* std::wcsstr(wchar_t*, const wchar_t*)â:
...... and many more similar errors.


g++ and gcc are installed properly as u can see below

himanshu@paradise:~/myUtils$ cat test.cc
#include <iostream>

using namespace std;

int main(){
        cout<<"I am executed.";
        return 0;
}
himanshu@paradise:~/myUtils$ g++ --version
g++ (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

himanshu@paradise:~/myUtils$ gcc --version
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Can someone tell me what is the problem ?? 

thanks

---

### Post by gord on 2006-03-15
you have to do
```
 sudo apt-get install build-essential
```
this installs all the relivent files you need

---

### Post by paradize on 2006-03-15
Thanks , that worked.

---

