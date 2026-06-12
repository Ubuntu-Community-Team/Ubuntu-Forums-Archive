---
title: "Programming, compiling C++ from terminal"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-11
Now that i have ubuntu set up nicely and feel fairly comfortable i would like to start doing some programming.  I did a year of C++ and 2 years of Java at school and i'm taking computer science at university so i'd like to go into next year feeling confident with my programming skills. 

 I have a very simple program i wrote several years ago in microsoft visual using C++ that calculates the area or perimeter of a given object chosen by the user.  I read a little how to that says all you need to do is g++ filename.cpp and it'll compile.  When i do this i get several errors!

Most are with regard to the header files, i know when programming with an IDE for java you need JDK profiles and then there's libraries and stuff, do i need to load these somewhere when compiling from the terminal? again with the header files there's one: windows.h is that necessary since i am using ubuntu?  

and silly question about my code, it says main() must return int, but i know this program runs fine when compiled in visual studio, and i remember in both C++ and Java out teacher told us to delete the contents within main**()**, i believe it's string args[], that might be Java i'm getting mixed up now haha

if anyone could answer these questions i would greatly appreciate aswell if anyone knows of any good tutorials send them this way!  I've attached my program if you need to reference it.

Thanks in advance, Alain

ps. sorry about the length!

---

### Post by Paul820 on 2007-07-11
Hello, you need to download build-essential. Just go to the terminal and type: sudo apt-get install build-essential

That will let you build your program. windows.h and stdafx.h will not work in ubuntu, they are microsoft specific files. Yes main() should return an int, although it does work without it it's good practice to put it in there, it's only a few extra letters. :) 

And to build from the command line, just put: g++ youfilename.cpp -o yourfilename

Hope this helps.

This should have been in the programming section, maybe the mods will move it, don't worry :)

---

