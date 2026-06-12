---
title: "[SOLVED] Compiling C programs with gcc"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by potatoehead64 on 2008-01-10
I've started learning C programing from scratch and managed to overcome quite a few problems by my own research, but I've one problem that is recurring:

after writing the code and saving the file, I use the recommended command in terminal

"gcc -o filename.c"   (i.e. the -o allowing the .out file to be named)

I'm getting "gcc: no input files"

However, if I enter the command without the "-o", the file does compile, but to the default "a.out" name. 

Why does this happen?

I have a 2nd computer that has Damn Small Linux installed and I get the same result. 

Any advice would be gratefully received. :)

---

### Post by metaknecht on 2008-01-10
"gcc -o filename filename.c"

you have to specify the output file name.

---

### Post by meindian523 on 2008-01-10
You need to use```
 gcc filename.c -o <whatever_output_file_you_want>
```

---

### Post by Joeb454 on 2008-01-10
meindian beat me to it...if you want the executable, that's the syntax, if you want the object file then use gcc -c file.c

---

### Post by Paul820 on 2008-01-10
If you need more information you can get it by typing in the terminal
> man gcc
All you need to know is right there.

---

### Post by Yellow Pasque on 2008-01-10
I believe the syntax is gcc inputfile -o outputfilename. If you're still confused..

I'll offer a practical example from the OSSv4 procedure in my sig. One of the steps is compiling a .c file into a .so library. The following line compiles a file named flashsupport.c into an object code file named libflashsupport.so
```
sudo cc <compiler flags> flashsupport.c -o libflashsupport.so;
```

---

### Post by meindian523 on 2008-01-10
Basically your problem is that the -o option needs to be followed immediately by the output filename,so when you put gcc -o filename.c,it takes filename.c as the name of the output file and therefore complains about lack of input files.

---

### Post by potatoehead64 on 2008-01-10
Brilliant! Thanks folks.

Doh! I hadn't picked up on the renaming protocol. Just done it and it worked. 

Martin

---

### Post by meindian523 on 2008-01-10
> **Paul820 said:**
> If you need more information you can get it by typing in the terminal
```
man gcc
```

All you need to know is right there.

+1

---

### Post by meindian523 on 2008-01-10
If that's all,plese mark the thread solved.

---

