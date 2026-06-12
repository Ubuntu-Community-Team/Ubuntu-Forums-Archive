---
title: "programming in C and C++"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-27
I want to program in C and C++ but I don't have the compiler necessary for ubuntu.  How can I get the compilers?

---

### Post by Sykil on 2005-10-27
What you need is gcc and g++.
```
sudo apt-get install gcc g++
```

---

### Post by racermike1967 on 2005-10-27
what does:
sudo apt-get install build-essential 
do?

---

### Post by Kyral on 2005-10-27
Nabs everything you need for compiling (STL libs, GCC, etc)

---

### Post by nitricacid on 2005-10-27
How hard is it to program in C or C++?
I have a how to book (learn C\C++ in 24hours) but never got around to reading it.
what are the basic to programming in C\C++?

---

### Post by cwaldbieser on 2005-10-28
[QUOTE=nitricacid]How hard is it to program in C or C++?
I have a how to book (learn C\C++ in 24hours) but never got around to reading it.
what are the basic to programming in C\C++?[/QUOTE]
C and C++ are different languages, so they tend to foster different styles of programming.  That said, they have a lot of the basic stuff you see in a lot of languages-- you can define variables and assign values.  You can control the flow of the program with "if" statements and loops.  You can define and call functions.

C APIs are pretty universal.  The languages are also both (in)famous for letting users manage their own memory usage.  It's not too hard to pick up the basics.  It can take a while (especially in C++) before you have an "Aha!" moment when you realize why things were done a certain way in the language.

---

### Post by nitricacid on 2005-10-28
could you suggest some books or sites for a C\C++ noob such as  myself, or does it all depend on what i want to write ??

---

### Post by Kyral on 2005-10-28
[www.cppreference.com](www.cppreference.com) is an awesome site for general reference, though you have to know the basics of the language first.

I always reccommend the "For Dummies" books because frankly they are very good, and humorous :D

---

### Post by nitricacid on 2005-10-28
Well I would like to learn some programming language so that I could help in developing of linux but that is prolly a long way away b4 i get into anything that advanced.

1 mor Q:
G++ & GCC are the  actual programs where you write your program, currect??

---

### Post by LHZ on 2005-10-28
Incorrect. 

When you write most software, you just fire up your editor of choice. Gedit is a good one (comes with Ubuntu), some prefer Emacs or vi, choose whichever one suits your style. You type the C (or C++ or Java, or Perl or whatever) code into the editor, and save it as a file (for C, you commonly save as a 'myprogram.c' file). Many editors have so called 'syntax highlighting', which colors commonly used words, and shows comments in a different color. These generaly make programming much more pleasant :) 

A compiler (such as GCC or G++) takes a programming language file (such as the aformentioned 'myprogram.c') and 'translates' itto machine code, the instructions your processor can understand. The result is an executable file ('myprogram'), which you can run to run your program. After you've compiled a program the source code is still there for you to make changes in. (Small tangent: a reason Linux is called 'Open Source' is that you could get the entire source code of Linux if you wanted to. You could then make changes, recompile, and have a personal version of Linux. If you wanted, and if you were that good :p ).

Some editor/compiler programs exist, which combine both functions, but in the Linux world it's common to use an editor for editing, and a compiler for compiling.

---

### Post by nitricacid on 2005-10-28
Thank you for that clearification :)

Another Q:
Where can I get the LInux Source Code?
I have searched google several times and could not find the linux source code.
I figured if i could 'lead by example' if you will, I could understand codeing a little better.

I have used Java & HTML to make web pages and I know those cards are prolly nothing like C\C++ I can still get a general idea of the code.

---

### Post by mostwanted on 2005-10-28
[QUOTE=nitricacid]Thank you for that clearification :)

Another Q:
Where can I get the LInux Source Code?
I have searched google several times and could not find the linux source code.
I figured if i could 'lead by example' if you will, I could understand codeing a little better.

I have used Java & HTML to make web pages and I know those cards are prolly nothing like C\C++ I can still get a general idea of the code.[/QUOTE]

You're not going to understand *anything* at all in the Linux source code if you have no prior programming experience...

[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by nitricacid on 2005-10-28
Well I feel like a goof.
I have been to that site be for but didn't pay much attention to it.

Sorry, I am a Re-Re sometimes.

---

