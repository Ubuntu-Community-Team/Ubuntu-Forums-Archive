---
title: "Compilation error"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by ahsonbol on 2007-11-18
Hi, 

I am trying to add a new system call. I did all the necessary (modify unistd.h,modify syscall_table.S,edit the Makefile,build the kernel) then I write a simple use program to use my system call. However, I got this error at compilation time

code.c:8: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;mycall&#8217;
code.c:8: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;arg1&#8217;
code.c:8: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;arg2&#8217;

my code is
```

#include <linux/errno.h>
#include <sys/syscall.h>
#include <linux/unistd.h>
#include <stdio.h>

#define __NR_mycall 320

_syscall2(int,mycall,int,arg1,int,arg2);

int main()
{
	int z;
	z=mycall(7,8);
	printf("%d\n",z);
	return 0;
}

```

Any help???

---

### Post by ddrichardson on 2007-11-18
Answered in your other post.

---

