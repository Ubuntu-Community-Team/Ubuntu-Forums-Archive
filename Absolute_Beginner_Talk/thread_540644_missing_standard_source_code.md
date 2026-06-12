---
title: "missing standard source code?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by duesen on 2007-09-01
Trying to compile a standard 'hello world' app, but it looks like the standard headers/libraries are missing:

#include	<stdio.h>

int main(void)
{
	printf( "Hello\n" );
	return 1;
}

$  gcc hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’


What do I need to install?

Thanks!

---

### Post by taurus on 2007-09-01
You need to install the build-essential package first before you can compile anything from source, including C program.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by duesen on 2007-09-01
> **taurus said:**
> You need to install the build-essential package first before you can compile anything from source, including C program.

```
sudo aptitude update
sudo aptitude install build-essential
```

Thanks! :))

By the way, what did I miss during the initial system installation?

---

### Post by yabbadabbadont on 2007-09-01
Nothing.  Development tools/libraries are not installed by default.

---

### Post by taurus on 2007-09-01
GCC or build-essential package doesn't install as default.  Therefore, you need to install it by hand after you install Ubuntu.

Did you install GCC by itself?  Bet you did.

---

