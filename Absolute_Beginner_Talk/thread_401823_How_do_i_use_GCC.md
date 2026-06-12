---
title: "How do i use GCC?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by SpanishFly25 on 2007-04-05
I know there is plenty of information about gcc in the forums. However, after searching for a while, i still have not found out how to open gcc.

I have Edgy 6.10 and i cant find anything called gcc anywhere. Do I just use the terminal to write my C++ code?

I have entered this into the terminal:
```
sudo apt-get install build-essential
```
and it says I already have it installed.

Could someone please tell me what to go to in order to start using gcc.
I am just starting with linux so step by step instructions would be helpful.
Thanks

---

### Post by ewankho on 2007-04-05
In the terminal type 'man gcc' to get more info on how to use gcc.

---

### Post by irwa82 on 2007-04-05
Hi,

gcc is just a compiler that compiles source files. You need to write your c code in an editor.

to use gcc then try the following

$ gcc -Wall -ansi filename.c -o filename

for c++ code you may need to do the following

$ g++ -Wall -ansi filename.cpp -o filename

The -Wall will give you all the warnings and the -ansi will make sure you are ansi compliant to enforce ansi compilant code i believe you also need the -pedantic option.

For the future I am not sure if programming is on topic in absolute beginners might want to try another category.

---

### Post by SpanishFly25 on 2007-04-05
Ohhhhh. I get it now.
Thanks guys.

Any are all editors pretty much the same or is there one i should consider over the rest?

---

### Post by M$LOL on 2007-04-05
I use SciTE, but that's just my preference. There are also IDEs such as KDevelop and Anjuta.

---

