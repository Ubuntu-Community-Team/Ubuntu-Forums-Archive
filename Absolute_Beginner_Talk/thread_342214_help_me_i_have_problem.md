---
title: "help me i have problem"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by programmer in linux on 2007-01-19
hello...

i try to compiler some file in C language  and when i write in terminal the command to compile file
they tell me 

program.c:1:19: [COLOR="Red"]error: stdio.h: No such file or directory[/COLOR]
program.c: In function &#8216;main&#8217;:
program.c:11: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

why i have these error ..? 

i use [COLOR="Red"]gcc -c file.c[/COLOR]  to compile my c file

---

### Post by taurus on 2007-01-19
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by programmer in linux on 2007-01-19
still i have  the problem

---

### Post by taurus on 2007-01-19
Well, let's have a look at your program.c then.

```
cat program.c
```

---

### Post by programmer in linux on 2007-01-19
jaber@jaber-laptop:~$ cat program.c
#include <stdio.h>

int main(){


        printf("hi hi hi");

        return 0;
}

---

### Post by programmer in linux on 2007-01-20
hello ](*,)

---

### Post by po0f on 2007-01-20
programmer in linux,

So, you're saying you have installed build-essential *correctly*, but you still don't have /usr/include/stdio.h?  This is a bug then.

I have a feeling you really don't have build-essential installed right.  Try again, just for completeness' sake.  Try installing libc6-dev as well:
```
[FONT="Courier New"]$ sudo aptitude update
$ sudo aptitude install libc6-dev build-essential[/FONT]
```

---

### Post by programmer in linux on 2007-01-20
thx =D>

---

### Post by MikeeAMD64 on 2007-01-23
Hello,

I am also having an issue compiling C++ programs, or any programs for that matter.  Whenever I try making the executable, I get the error:

```
/lib/libc.so.6: file not recognized: File format not recognized
```

I have gcc, g++, libc6-dev, and build-essential installed but yet I'm still having a problem with that.  I have also tried:

```
sudo apt-get --reinstall install libc6-dev
```

But that gave me an error.

I don't wish to remove libc6-dev, because it has a lot of dependencies, and I don't wish to break anything (more than it is already broken).

I'm using edgy on AMD64.

---

