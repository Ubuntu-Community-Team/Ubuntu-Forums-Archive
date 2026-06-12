---
title: "I'm embarrassed to ask, but how do I get gcc to compile?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by smegmaster on 2006-07-03
I just installed Ubuntu and tried to compile a quick "Hello, World" program to check gcc, but my file won't compile. Here's the code:

```
#include <stdio.h>

int main(void)
{
	printf("Hello, World!\n");
	return 0;
}


```

And here's the error:

```
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

```

Any help? Thanks!

---

### Post by catlett on 2006-07-03
Don't be embarassed. This is an ongoing issue with ubuntu. because they keep the install to one cd they leave stuff out. one of the things is gcc compilers. most people think it is crazy to ship a linux distro without compilers but we are not the ones in power.
Anyways install the compilers with this package. In the terminal 
```
sudo apt-get install build-essential
```

---

### Post by claydoh on 2006-07-03
oops, ya beat me to the punch :)

---

### Post by smegmaster on 2006-07-03
I thought I'd already installed gcc from Synaptic, but what you posted did the trick. Thanks!

---

