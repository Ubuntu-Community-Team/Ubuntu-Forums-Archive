---
title: "C compiler"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by a1010100m on 2006-08-07
When I try to compile a program, there is a notice that my compiler is not a good compiler...I am using ubuntu 6.06...Ths. ( sory about my english, that`s not my primary language ). Ths.

What to do with that...???

---

### Post by taurus on 2006-08-07
Open a terminal (Applications -> Accessories -> Terminal) and type

```

sudo apt-get install build-essential

```
That's all you need to compile something...

---

### Post by tribaal on 2006-08-07
What command / program do you use to compile you C source code? 

What I use is "gcc", which should be able to compile your C source code into an executable.
Try to run "man gcc" from a terminal. If that doesn't work, make sure you have gcc installed first: 
```
sudo apt-get install gcc
```

The the first lines of the man page should help you out with the syntax. Basically I use ```
gcc <sourcefile> -o <executable filename>
```, and it works fine to compilce C source code...

Just make sure you read man GCC, it's really the ultimate ressource. :)

Hope this helps...

- trib'

---

### Post by a1010100m on 2006-08-07
My mistake...first time he asked from me to upgrade gcc, and I unistall it. thanks.

---

