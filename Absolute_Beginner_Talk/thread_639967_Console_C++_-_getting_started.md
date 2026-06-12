---
title: "Console C++ - getting started"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by superjacent on 2007-12-13
I'm in this forum as I'm relatively new to Linux.   I'm learning C++, all console apps at the moment, via Windows.   Now I'm wanting to try it from Linux.   Can somebody point me to the right software tool, editor, and then how to configure it to compile to an executable all from within the editor or ide.   

Any help appreciated.

---

### Post by snickers295 on 2007-12-13
Hello.
if you want some compiler and stuff in the console type ```
sudo apt-get update
sudo apt-get install build-essential 
```
and to use the c++ compiler type ```
g++ <filename>
```
and just use gedit for a editor.

---

### Post by hfranco on 2007-12-13
To be more specific,

In order to compile C++ code you’re going to need a compiler. In Linux you can do this with the g++ compiler. 

We’ll begin by writing a simple Hello World program with our vim editor or any other editor you prefer:

```
#include <iostream>
using namespace std;

int main()
{
cout<<"Hello World\n";

return 0:
}
```

I'll save it as hello.cpp. Now you can compile it via the command:
```
g++ hello.cpp -o hello 
```

g++ calls hello.cpp and converts it into a binary executable file with the -o command. The hello file is the binary executable.You can now run the executable file with the command ./hello

---

### Post by superjacent on 2007-12-13
Thank you both.   That "Hello World!" program certainly gets around.......

---

### Post by snickers295 on 2007-12-14
> **superjacent said:**
> Thank you both.   That "Hello World!" program certainly gets around.......
ya it does.
i recall a thread that has a hello world program in every programing language.

---

