---
title: "GCC compiling problem at a simple c++ program"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-20
I try to compile the simplest c++ program, called hello.c by ```
gcc hello.c
``` and the errors are: ```
hello.c:1:21: error: iostream.h: No such file or directory
hello.c: In function ‘main’:
hello.c:3: error: ‘cout’ undeclared (first use in this function)
hello.c:3: error: (Each undeclared identifier is reported only once
hello.c:3: error: for each function it appears in.)
hello.c:3: warning: return type of ‘main’ is not ‘int’

```. I have gcc installed. There is no error if I use stdio.h and print but i'd like to use iostream too.

---

### Post by philippe_carlo on 2006-07-20
> **FuzZy2006 said:**
> I try to compile the simplest c++ program, called hello.c by ```
gcc hello.c
``` and the errors are: ```
hello.c:1:21: error: iostream.h: No such file or directory
hello.c: In function ‘main’:
hello.c:3: error: ‘cout’ undeclared (first use in this function)
hello.c:3: error: (Each undeclared identifier is reported only once
hello.c:3: error: for each function it appears in.)
hello.c:3: warning: return type of ‘main’ is not ‘int’

```. I have gcc installed. There is no error if I use stdio.h and print but i'd like to use iostream too.

```
sudo apt-get install build-essential
```

---

### Post by Sonic Alpha on 2006-07-20
> **FuzZy2006 said:**
> hello.c:3: warning: return type of &#8216;main&#8217; is not &#8216;int&#8217;

This one should be because you created a void main() and not an int main()

Change it to int, and just before the end add a "return 0;"

ie:

```
int main()
{
//lots of code

return 0;
}
```

You also need to add the "using namespace std;" thing to use "cout" instead of the longer output line.

Plus, it looks like a C file, and not a c++ one (.cpp).

---

### Post by crystal on 2006-07-20
Name the file hello.cpp and then use g++, the C++ compiler of GCC. Currently the file is being compiled as a C program, hence the C++ standard library does not exist.

---

### Post by FuzZy2006 on 2006-07-20
```
sudo apt-get install build essential
```
Nothing happened
```
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by FuzZy2006 on 2006-07-20
I don't think that may be the problem cos I copied the exercise from a C++ book, but I did as you said and there remains the problem with iostream unsolved, the errors now are ```
hello.c:1:21: error: iostream.h: No such file or directory
hello.c: In function ‘main’:
hello.c:6: error: ‘cout’ undeclared (first use in this function)
hello.c:6: error: (Each undeclared identifier is reported only once
hello.c:6: error: for each function it appears in.)

```

---

### Post by FuzZy2006 on 2006-07-20
Wow , thanks, now it works. I didn't now that I should use that g++.

---

