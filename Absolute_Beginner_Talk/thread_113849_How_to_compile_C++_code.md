---
title: "How to compile C++ code?"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by chimera on 2006-01-07
I have build-essential and gcc and everything else people told me I needed to compile C++ code, but I still don't know how to use those programs to compile my code. Any help would be appretiated.

---

### Post by bored2k on 2006-01-07
Regular usage would be ```
g++ code.cpp -o code
```
To ease this process, one would recommend you to get an IDE like **anjuta**, which is quite good and easy to understand.
[[IMG]http://img218.imageshack.us/img218/189/a3vk.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=a3vk.jpg)
```
sudo apt-get install build-essential gcc-3.4 g++-3.4 anjuta
```

---

### Post by chimera on 2006-01-07
Thanks for the help, I only needed the first command-line you gave me, but that IDE seems pretty nice too, I like it:D (definetely better than vim, which I used before lol)

Another question, how do I make it compile it into a windows executable instead of a linux one?

---

### Post by cwaldbieser on 2006-01-07
[QUOTE=chimera]Thanks for the help, I only needed the first command-line you gave me, but that IDE seems pretty nice too, I like it:D (definetely better than vim, which I used before lol)

Another question, how do I make it compile it into a windows executable instead of a linux one?[/QUOTE]
You have to set up a cross-compiler.  I do not know an easy way to do this.  Your best bet would probably be to ask on the programming forum.  Googling returns a lot of HOWTOs, but they are a little daunting.

Of course, the easiest way is probably to just get a compiler like mingw ([http://www.mingw.org/]("http://www.mingw.org/")) and just building it on a Windows machine.

---

### Post by chimera on 2006-01-07
I know, I have windows too on this machine, but having to reboot to switch between Ubuntu and windows is kinda pointless when I can do it all from Ubuntu.

---

### Post by elmoosecapitan on 2008-06-19
Thanks for the help guys!

---

