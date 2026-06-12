---
title: "Something's wrong with my C Library paths"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by goblue on 2008-02-15
...and I'm still a bit too green with Ubuntu to know what to do.

I'm compiling some simple C files with GCC in a bash shell.  When I try to compile, it's not finding my C standard libraries (like <stdio.h>).  I'm not sure what file to edit (and what to put there) to get gcc to find my libraries.  I'm also confused about why this started horking-up in the first place (I recently did a batch of Ubuntu automatic-updates, which screwed up my GRUB loader as well... grr.  Good thing I backed that up.  Although I'm not sure the updates were to blame.)

A simple C file:
```
#include <stdio.h>

int main()
{
    printf("Here's my sample file that should compile easily.\n");
    return 0;
}
```

...and here's what I get from the shell:

```
$ gcc -o foo foo.c
foo.c:1:19: error: stdio.h: No such file or directory
foo.c: In function &#8216;main&#8217;:
foo.c:5: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
$
```

**??**

Thanks,

- Mike

---

### Post by Cypher on 2008-02-15
You need the LIBC6-DEV package..so
```

sudo apt-get install libc6-dev
gcc -o foo foo.c

```

---

### Post by goblue on 2008-02-15
Did the trick.  Thanks a bunch.

---

