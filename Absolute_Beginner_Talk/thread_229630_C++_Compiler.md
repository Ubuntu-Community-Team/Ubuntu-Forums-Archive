---
title: "C++ Compiler"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Icon41 on 2006-08-04
I know some basic c++ in windows but im clueless on how it works in linux, and I cant find Bloodshed Dev c++ for linux, can someone point me in the right direction

---

### Post by ColdDeath on 2006-08-04
If you have written helloword.cpp and saved it in your home directory, you can run:
```
g++ helloworld.cpp
```
In the terminal, this will compile it to a file called a.out.

To run your program, run:
```
./a.out
```
To do this you will will need compilers and other stuff which you can install with this command:
```
sudo apt-get install build-essential
```
If you want an IDE I suggest you try Anjuta:
```
sudo apt-get install anjuta
```
Have fun!

Just say if you need any help.

Edited.

---

### Post by avtolle on 2006-08-04
I think there's a typo; should be build-essential.

---

### Post by BornLoser on 2006-08-25
When compiling in Anjuta is it possible to save as the .cpp format or just the .cc format that is used when writing a C++ source file? 

I'm curious because my current C++ professor uses Dev-C++ in Windows and has asked for all of our submissions to be in the .cpp format. 

Also, can anyone point me in the direction of a good 'getting started' guide on anjuta?

---

### Post by Jerome36 on 2006-08-25
If you're looking for an IDE there's a few options.  Many are available in the "Add/Remove" Programs.  [KDevelop](http://www.kdevelop.org/) seems to be fairly popular.  I do most of my programming in Windows though, including using Dev-C++.

---

