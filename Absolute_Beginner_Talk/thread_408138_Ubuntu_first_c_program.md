---
title: "Ubuntu first c program"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by jabbertrex on 2007-04-12
I installed Ubuntu and installed the build-essential package using Symantec Package Manager

When I write a simple C program, one compies and the other gives error

Example I: works fine
#include <stdio.h>
int main(int argc, char *argv[])
{
printf("# of args %d \n", argc);
}

Example II: gives error in compile
#include <stdio.h>
int main(int argc, char *argv[])
{
printf(" %s \n", argv[0]);
}

Example 2 gives me error: argv undeclared (first use in the function)

I am using Ubuntu gcc 4.0.2 20050808 prerelease version that came with the book.

This is a very simple program. Why I am getting argv undeclared error.

Thanks,
Jay

---

### Post by yabbadabbadont on 2007-04-13
Both should have produced a compile error.

```
int main(argc, char *argv[])
```
Should be
```
int main(int argc, char *argv[])
```

---

### Post by jabbertrex on 2007-04-13
I still get the same error: (gr8 pair of eyes though :-)

The exact code is
#include <stdio.h>

int main(int argc, char *argv[])
{
printf("%s ", argv[0]);
}

---

### Post by yabbadabbadont on 2007-04-13
```
/home/daffy/code/tmp $ cat go.c
#include <stdio.h>

int main(int argc, char *argv[])
{
printf("%s\n", argv[0]);
}
/home/daffy/code/tmp $ gcc go.c -o go
/home/daffy/code/tmp $ l
total 12
-rwxr-xr-x 1 daffy daffy 6606 2007-04-12 23:33 go*
-rw-r--r-- 1 daffy daffy   82 2007-04-12 23:33 go.c
/home/daffy/code/tmp $ ./go
./go

```
You must be doing something wrong somewhere...  :?

---

### Post by jabbertrex on 2007-04-13
You are correct - it was a silly typo (agrv instead of argv) - can't believe wasted your time and my time too on this.

Thanks for your help.

---

