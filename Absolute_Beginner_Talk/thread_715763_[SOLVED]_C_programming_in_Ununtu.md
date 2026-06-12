---
title: "[SOLVED] C programming in Ununtu"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by cybo on 2008-03-05
I'm trying to learn C (one of the reasons I installed Ubuntu). I'm trying to run a basic program:

#include <stdio.h>
#include <stdlib.h>

int main(void) {
  printf("Hello world\n");
  return (0);
}

then I compile it as follows:
gcc -Wall -Werror helloworld.c

and I get the following response from the compiler: 

helloworld.c:1:19: error: stdio.h: No such file or directory
helloworld.c:2:20: error: stdlib.h: No such file or directory
cc1: warnings being treated as errors
helloworld.c: In function ‘main’:
helloworld.c:5: warning: implicit declaration of function ‘printf’
helloworld.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

it seems to me that the environment for C is not set up. Can anyone tell me how to do that? Please keep in mind that I'm new to Ubuntu and not very experienced in programming.

I also have another question about the gcc package. I looked through the packages I have installed for gcc, and i found 2. 
1) Package: gcc, Installed version: 4:4.1.2-9ubuntu2, Latest version: 4:4.1.2-9ubuntu2
2) Package: gcc-4.1, Installed version: 4.1..2-16ubuntu2, Latest version: 4:4.1.2-26ubuntu2.

The first one is a dependency package (don't know what that means). I'd like to keep my Ubuntu clean, so if I don't need a package I just remove it. I want to know if I need both of these packages and if I can remove one of them?

Again, keep in mind I'm new to Ubuntu, computers and programming.

---

### Post by Siph0n on 2008-03-05
try sudo apt-get install build-essential
That will install some headers you need... I believe...

---

### Post by Cypher on 2008-03-05
Install the package with the headers
```

sudo apt-get install libc6-dev

```

If you installed the compilers using the "build-essential" meta-package, then you should leave the packages that were installed alone. Unless you KNOW you don't  need a package and want to remove it..

---

### Post by cybo on 2008-03-05
> **Cypher said:**
> Install the package with the headers
```

sudo apt-get install libc6-dev

```

If you installed the compilers using the "build-essential" meta-package, then you should leave the packages that were installed alone. Unless you KNOW you don't  need a package and want to remove it..

Thanks. It worked. I appreciate it.\\:D/

---

### Post by DrMega on 2008-03-05
Have you tried one of the IDE's? Code::blocks is ace. Geany is good also. They will save you having to compile and link at the command line (unless of course you want to do it from the command line, which is fine of course).

Coming from a Windows development background, I like Code::blocks because it has most of the nice stuff I've grown used to, like syntax colouring, code completion, integrated debugger etc, but its horses for courses really. Some people prefer to do it all from the command line.

---

