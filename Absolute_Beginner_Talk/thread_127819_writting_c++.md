---
title: "writting c++"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-02-09
Hey ubuntu,
      I would like to write a c++ program (as I am about to start learning c++ in school) with the tools available in ubuntu. How do I go about doing that. 
      In kdevelop I went to new, named to the file something, then typed in the code. After this I tried to look for the compile command but was not able to find it. For the file name should I have written something.extension? 
  

cheers

---

### Post by bored2k on 2006-02-09
Are you using KDE?  The thing about KDevelop is that it's great for projects, but it's kinda complicated to do work with the simple C++ you and I work with. If you want to work with an IDE like Kdevelop, I'd suggest Anjuta (make sure your files are named .cc or .cpp). If you just want a simple text editor with syntax highlighting, just pick anyone.

If you work with an editor, to compile a program, the appropiate command would be:
```
g++ code.cpp
```
To run it
```
./a.out
```
Although that might as well be
```
g++ code.cpp -o code
```
```
./code
```

Note: you would want to install the package *build-essential* and possibly *libtool* (if you ever work with projects in Ajuta).

[http://www.ibiblio.org/obp/thinkCS/cpp/english/](http://www.ibiblio.org/obp/thinkCS/cpp/english/)

---

### Post by mwanafunzi on 2006-02-09
thanks for the help..
I will try anjuta out. 
thanks again

---

