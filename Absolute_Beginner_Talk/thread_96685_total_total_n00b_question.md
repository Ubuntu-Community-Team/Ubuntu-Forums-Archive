---
title: "total total n00b question"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by softwarepirate on 2005-11-29
How do i open gcc?:confused: :confused:  Ive been searching google for two days on that question.

---

### Post by invalid on 2005-11-29
How do you open it? I'm afraid this is a misleading question.. 

You can install it with```
sudo apt-get install gcc
```or```
sudo apt-get install build-essential
```would be better, which includes all the things you need for basic compiling and making.

If you are trying to use it to compile, try man gcc for options.

Hope this is what you are looking for,
Cb

---

### Post by softwarepirate on 2005-11-29
Yeah but what do i use to make the program like gedit or what? that's what i dont understand the rest i understand.

---

### Post by invalid on 2005-11-29
To edit source, use your favorite editor (nano, gedit, whatever) and save it as source.c

To compile a C program, open a terminal and type```
gcc -o programname source.c
```

Afterwards, you can run the program with```
./programname
```

Cb

---

### Post by Brunellus on 2005-11-29
use your favorite text editor  Gedit, nano, vim, emacs....

---

### Post by softwarepirate on 2005-11-29
Thanks :D

---

### Post by edm00se on 2005-11-29
If you are looking for some ideas on where to get started looking at some of the available options, I recommend [this link]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html#7"). It is the Programming and Development section of "The table of equivalents / replacements / analogs of Windows software in Linux".

Please note, I am not promoting that Windows is the place to code, but rather this page (linked above) is a fairly decent listing of app's.

Hope it helps.

---

