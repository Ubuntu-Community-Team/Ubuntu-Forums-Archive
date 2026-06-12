---
title: "C++ Compiler"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-12-02
I'm Starting to learn C++ and world like to know whats the best compiler to use under ubuntu. i don't mind weather its terminal based, or a GUI just as long as it is easy to use.

any suggestions?

---

### Post by LLRNR on 2006-12-02
gcc ? g++ ?

I think doing ```
sudo aptitude install build-essential
```should be enough... but they're command based.

---

### Post by Jamesbowden on 2006-12-02
thanks i installed it, so say i have a file on my desktop called "example.cpp" what would i have to type at the terminal to make it run.

---

### Post by LLRNR on 2006-12-02
I only use gcc:
```
gcc -o example example.c
```
You can find out a brief description of the options you can use with the compilers with **gcc --help | more** and **g++ --help | more** or see their man pages: **man gcc** and **man g++**.

LLRNR

---

### Post by lamego on 2006-12-02
Your question is not about Ubuntu, it is about C/C++ developing in Linux.
If you google for it you will probably find much more tutorials and help, anyway here is one:
[http://www.arachnoid.com/cpptutor/setup_unix.html](http://www.arachnoid.com/cpptutor/setup_unix.html)

---

### Post by Jamesbowden on 2006-12-02
Thanks, Does any one know of a good UI based C++ compiler with a built in text editor, that how i used to work with other languages in windows.

---

### Post by maaronB on 2006-12-02
Anjuta is good for C++ beginers.

---

### Post by 56phil on 2006-12-02
You may want to try Anjuta or Eclipse.

---

### Post by Jamesbowden on 2006-12-02
i have ajunta IDE but i have no idea how to compile from it.

---

### Post by maaronB on 2006-12-02
In anjuta compiling is very simple. 

Save the project.
Then go to Build menu and choose Build (or hit F11)

---

### Post by maaronB on 2006-12-02
A quick walk through of a very simple Hello World Program

click File->New
choose C++ source file
name it "hello.cc" or "hello.cpp"
click OK
type in something like
```
#include <iostream>
using namespace std;

int main()
{
cout << "hello world";
}
```
click on File->Save As 
call it whatever.
click on Build->Build
then 
Build->Execute


If everything is installed correctly that should be all you have to do.

---

### Post by HokeyFry on 2006-12-02
i dont know about the rest of you but every time i try to use some sort of IDE for C/C++ i get an error along the lines of something is wrong with the makefile. I am not that advanced in C/C++, i dont know much about make or makefiles, so i just use gcc/g++ from the command line. it works for learning, and its not complicated.

---

### Post by Jamesbowden on 2006-12-02
Thanks, i have already done my first hello world program. although i did:

```
#include <iostream>

int main()
{
cout << "hello world";
}
```

what does the:

```
using namespace std;
```

do.

---

### Post by HokeyFry on 2006-12-02
umm when your using the C++ standard u usually have to type, for example, instead of 'cout' you type

```
std::cout
```

using namespace std; takes care of that. depending on the compiler you use though it might automatically assume you are using the standard namespace


if im wrong someone correct me

---

### Post by maaronB on 2006-12-02
Did your program compile correctly?  
Whenever I try it in Anjuta I get scope errors.

I am not going to pretend that I am advanced enough to really understand what the namespaces are all about, but I thought that if anything comes from the Standard Library it had to be declared as std in some way.

---

### Post by HokeyFry on 2006-12-02
thats what 'using namespace std;' does. and i believe some compilers will assume that regardless of whether or not you specify it

---

### Post by Jamesbowden on 2006-12-02
i cant even find where to compile in Anjuta

---

