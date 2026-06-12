---
title: "Need help with gcc compiler"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by nsudharshan on 2007-06-22
Hi ppl,
  I recently installed the much famed Ubuntu Feist Fawn & I want to compile & run C & C++ programs using the gcc compiler which I believe is already installed (Checked up in Synaptic - only removal option exists, in which case my guess is gcc compiler collection is installed !!). However, when i try to compile a simple C program:

// File name: sample.c //

#include<stdio.h>
int main()
{
    printf("Working");
    return 0;
}

When i type *gcc sample.c* in the terminal (sample.c is stored in my home folder only), it gives an error saying:
error: stdio.h: No such file or directory

I also tried changing the header file to <stdio> alone, but to no avail.
PL. help...

---

### Post by Bachstelze on 2007-06-22
YOu must install the package *build-essential*.

---

### Post by LaRoza on 2007-06-22
```
sudo aptitude install build-essential
```

I don't know if you know this already, but remember to use g++ for C++ programs.

Also, if you add -o fileName, the file you create will have that name.

In short:
```

g++ source.cpp -o program.exe

```

It is the same for gcc. Also, the file extensions are not needed, but I add them to clarify what kind of file it is.

---

### Post by terabite on 2007-06-22
U shud try installing '**libglib2.0-dev**' and '**libglib2.0-0-dbg**'.

---

