---
title: "I need help...I can't use c++ and I have to use it now!!"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by rednauj on 2008-04-04
Hello, I'm new to this ubuntu and I don't have windows. I need to make a c++ program for next week(for my programing class) and I don't know why ubuntu don't compile the c++ I used with wine.
If you know how I can make programs in c++ in ubuntu I'll be grateful. Please be specific cause I really new to this ubuntu.

---

### Post by Tatty on 2008-04-04
[https://help.ubuntu.com/7.10/programming/C/build-essential.html](https://help.ubuntu.com/7.10/programming/C/build-essential.html)

This will let you produce ubuntu software using c++.  If you want to make windows software then ive no idea im afraid...

---

### Post by Laser Dude on 2008-04-04
You can also use g++ (or gcc, I *think* gcc can compile c++).  It will compile a file that can be executed like you would be used to in Windows.

```
sudo apt-get g++
```

You can then compile your programs by navigating to the directory in terminal and typing:

```
g++ [FILE] -o [OUTPUT]
```

Where FILE is the file or files that you want to compile, and output is the name of the file that's outputted.

---

### Post by rednauj on 2008-04-04
so FILE is like TEST.cpp and OUTPUT TEST?

---

### Post by rednauj on 2008-04-04
juan@juan-desktop:~$ sudo apt-get g++
E: Invalid operation g++

That's what says.

---

### Post by AustinC on 2008-04-04
sudo apt-get install g++

is probably what was meant

---

