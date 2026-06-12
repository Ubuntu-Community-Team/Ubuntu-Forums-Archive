---
title: "C compiler"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by infernus_crusher on 2007-08-18
I'm a uni student studying C and I usually compile with this code

gcc -o filename filename.c

and running it with

./filename

My C codes usually begin like this:

#include <stdio.h>

int main()
{

}

I did that in Ubuntu and got a message saying no such file <stdio.h>. It doesn't seem to recognise the library for some reason.

Any help would be appreciated.

---

### Post by taurus on 2007-08-18
How did you install GCC on your machine?  Did you install GCC by itself or did you install the build-essential package?

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by infernus_crusher on 2007-08-18
It's included when I installed Ubuntu. The GNU C compiler.

---

### Post by taurus on 2007-08-18
Try installing the build-essential package first and then compile that c program again.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by infernus_crusher on 2007-08-18
It works now. Thx a lot.

---

