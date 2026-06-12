---
title: "cc, gcc, g++, etc."
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by cumptrnrd on 2006-03-10
How do I set up cc, gcc, and g++ and things like that so I can compile CPP programs and stuff?

I got cc, gcc, g++, and make through Synaptic, but when I try to compile a program, I get toonnnnnnnnnnsssssss of lines or errors.

There shouldn't be anything wrong with my Makefile or any of my files because I was able to compile and run this program on the school computers...

- Chris

---

### Post by gerbman on 2006-03-10
Trying installing the "build-essential" package. What errors, if any, do you get after doing that?

---

### Post by cumptrnrd on 2006-03-10
I won't post all of them, but they are mostly something like this:

/home/christopher/Documents/CS 225 - MP1/main.cpp:55: undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
/home/christopher/Documents/CS 225 - MP1/main.cpp:55: undefined reference to `std::cout'
/home/christopher/Documents/CS 225 - MP1/main.cpp:55: undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/home/christopher/Documents/CS 225 - MP1/main.cpp:57: undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
/home/christopher/Documents/CS 225 - MP1/main.cpp:57: undefined reference to `std::cout'
/home/christopher/Documents/CS 225 - MP1/main.cpp:57: undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/home/christopher/Documents/CS 225 - MP1/main.cpp:59: undefined reference to `std::cout'
/home/christopher/Documents/CS 225 - MP1/main.cpp:59: undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'

Do I have to install like the C++ library and stuff like that?  It kinda looks like it can't like figure out those standard functions or something, but I don't know...  I can't really tell...

---

### Post by gerbman on 2006-03-10
[QUOTE=cumptrnrd]Do I have to install like the C++ library and stuff like that?[/QUOTE]

Yup, I think so. Package "libstdc++6".

Cheers!

---

### Post by cumptrnrd on 2006-03-10
sudo apt-get install libstdc++6?

It's already installed.  libstdc++5 is installed also, because I used it to install the newest version of Firefox.

Could it be something else I have to install?

---

### Post by Nord on 2006-03-10
Hi

Are you using g++ to compile a C++ program?
Did you include "using namespace std;" below the include file in your code?

I just started programming in C++ and I had similar problems.
Nord

---

### Post by BoyOfDestiny on 2006-03-10
Well, if you already have build-essential installed (you did install it right?). You might want to test some other code than something you've just written... Unless you know it's perfect and compiles/runs elsewhere that is... =)

---

### Post by cumptrnrd on 2006-03-10
Yeah, I did install that build essential thing.  I also installed libstdc++6 and make.

The code I'm trying to compile is from an assignment I already turned in.  I'm just trying to get the compiler and stuff to work so I can write my programs on my laptop now instead of in the school computer labs.  My code and Makefile have already compiled successfully on the school's Sun Unix machines.

---

### Post by Luke on 2006-03-10
could it be that you're using
```
gcc helloWorld.cpp
```

rather than
```
g++ helloWorld.cpp
```

when i do it with 'gcc' i get errors like yours. with 'g++' it works fine.

---

### Post by daredevil on 2006-03-11
try this

```
sudo apt-get install build-essential
```

---

### Post by cumptrnrd on 2006-03-22
I installed the build-essentials and the libstdc++6 thing, and I tested it using the following program:

#include<iostream>
using namespace std;

int main()
{
    cout << "Hello World!" << endl;
    return 0;
}

Now it compiles just fine... but when I run it, there's no output...  Shouldn't it output "Hello World!"?

---

### Post by gos1 on 2006-03-22
Hi ; 
 I am trying to run a simple hello world code on kdevelop too. (if you know a better c++ editor please let me know). 
 when I click build I get 
---------------------
cd '/home/cem/deneme/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
make all-recursive
Making all in src
make[2]: Nothing to be done for `all'.
*** Success ***
----------------------------
but when I click execute application I get this error messages. Does any one know why  _ 
-----------------------------
/bin/sh:konsole: command not found:
***exited with status:127***
-------------------------------

---

### Post by belikralj on 2006-03-25
I'm sort of new to both Linux and C programming. Though I have not tried to run any C++ programs on my machine, my C programs work just fine. I'm sure you already tried this but I don't know of a different way to get more libraries yet, so I suggest you try to use Synaptic Package Manager or Add Applications, in advanced mode to get more libraries through the X Window, doing a search or going through the developers section.  Good luck, sorry I coultn't help more.

---

### Post by icyisamu on 2006-03-25
> **cumptrnrd]I installed the build-essentials and the libstdc++6 thing, and I tested it using the following program:

#include<iostream>
using namespace std said:**
> 

Hi, this is my output. It should output into the terminal.

```
serph@laptop:~$ g++ -o  something.o something.cpp
serph@laptop:~$ ./something.o
Hello World!
```


[QUOTE] 	Hi ;
I am trying to run a simple hello world code on kdevelop too. (if you know a better c++ editor please let me know).
when I click build I get
---------------------
cd '/home/cem/deneme/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k
make all-recursive
Making all in src
make[2]: Nothing to be done for `all'.
*** Success ***
----------------------------
but when I click execute application I get this error messages. Does any one know why _
-----------------------------
/bin/sh:konsole: command not found:
***exited with status:127***
-------------------------------

For this, it depends on your needs for an IDE. If its just a simple terminal program, try using g++ or gcc and see if it compiles correctly.

---

### Post by Luke on 2006-04-11
do you have libtools installed?

if not,

```
 sudo apt-get install libtools
```

---

