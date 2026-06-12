---
title: "Problem compiling a C++ program"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Arghesis on 2007-05-19
Hello there,

I'm new to Linux. I'm using a Kubuntu Feisty. I pretty much got the hang of it. I like it a lot.
Hopefully i'll get better and better in time, but now I'm just at the newby rank.

Here's my problem.

I installed build-essentials, and I wanted to do just a little C++ program to see if it works.
######################################
#include <iostream>
using namespace std;

int main() {
	cout << "Hello World!\n";
	cin.get();
	return 0;
}
######################################

I enter Konsole and type : gcc hello_world.cpp 
Then I get this : 

pavel@pom:~$ gcc hello_world.cpp
hello_world.cpp:8:2: warning: no newline at end of file
/tmp/ccMsAGXF.o: In function `__static_initialization_and_destruction_0(int, int)':
hello_world.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccMsAGXF.o: In function `__tcf_0':
hello_world.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccMsAGXF.o: In function `main':
hello_world.cpp:(.text+0x8e): undefined reference to `std::cout'
hello_world.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
hello_world.cpp:(.text+0x9a): undefined reference to `std::cin'
hello_world.cpp:(.text+0x9f): undefined reference to `std::basic_istream<char, std::char_traits<char> >::get()'
/tmp/ccMsAGXF.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

If anyone could help me with this I would really much appreciate it.
Thanks.

PS: I want to learn programming in C++ and I've been using Borland 5 on my Windows. It compiles the *.cpp, makes an *.exe file and everything is ok.  A bit lost in Linux. I know the procedure is to be the same.

---

### Post by kaamos on 2007-05-19
gcc is for C, use g++ for C++

---

### Post by Arghesis on 2007-05-19
It appears to work. When I do g++ hello_world.cpp,  it makes an executable file called 'a.out'.
In the console it doesn't display anything, even if I wrote cout<<"hello";

Could you pls help me understand what's going on ?

---

### Post by kaamos on 2007-05-19
Can't really help you since your code seems to be working fine for me.
```

$ g++ -Wall test.cpp
$ ./a.out 
Hello World!
something
$

```
Make sure you are executing the right file.

---

### Post by Arghesis on 2007-05-19
Thank's for your help.

I got it ;)

---

