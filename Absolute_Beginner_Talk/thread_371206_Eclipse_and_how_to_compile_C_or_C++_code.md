---
title: "Eclipse and how to compile C or C++ code"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-26
I recently was able to get the proper C and C++ plug-ins for my Ubuntu computer for Eclipse but I cannot get the code to compile. 


I have tried to do a very simple program 

#include <iostream>
using namespace std;
int main()
{
        cout << "Hello World" << endl;
        return 0;
}// end main



But every time it give me the error

make clean all 
make: *** No rule to make target `clean'.  Stop.

I know that this code compiles in Microsoft Visual Studio and in g++. I would greatly appreciate if you could walk me through the steps about how to compile C or C++ file(s) so that I won't have problems again. 

Thank you


:popcorn:

---

### Post by netkid91 on 2007-02-26
You don't have an entry in the makefile for clean, simple enough.  Try just "make" or "make all".

---

