---
title: "Missing gcc headers on 7.04"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by resistantgnome on 2007-07-10
I recently did a clean install(format+default installation) of ubuntu 7.04. 

GCC Version 4.1.2 is installed(checked through gcc -v). But when I tried compiling a simple code
```

#include <stdio.h>

int main(void)
{
  printf("Hi");
  return(EXIT_SUCCESS);
}

```

It gave an error for missing header(stdio.h). 

Even after manual search I coundn't find stdio.h in the system. Isn't gcc completely installed in default installation?

---

### Post by loell on 2007-07-10
install build essential , for the complete development environment

```
sudo apt-get install build-essential
```

then compile your code again :)

---

### Post by Rui Pais on 2007-07-10
hi,
stdio.h should be on: /usr/include/stdio.h and is installed by the package libc6-dev.

How do you installed gcc? You must install it with:
```
sudo apt-get install build-essential
```

---

### Post by jnorthr on 2007-07-10
Same problem here. see my post under 'programming'.

---

