---
title: "gcc problems"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by billvb on 2006-05-14
Hello,

I have a file called test.c.  It contains just:

int main() { return 0; }


and whenever i try to compile it:

bill@cheese:~/Development$ gcc -o test test.c
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

or, if i include <iostream.h>:

bill@cheese:~/Development$ gcc -o test test.c
test.c:1:22: error: iostream.h: No such file or directory

What do i have to do to get gcc to function properly?  This has been driving me crazy all day!  Any help would be great, thanks!
-Bill

---

### Post by Sef on 2006-05-14
To compile, you need to install build-essential.

In Gnome, open the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get install build-essential

---

