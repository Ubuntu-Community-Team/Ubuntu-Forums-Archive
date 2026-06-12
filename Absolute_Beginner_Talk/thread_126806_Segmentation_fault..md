---
title: "Segmentation fault."
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by nixclusive on 2006-02-07
When I compile a program which contains:

stdio.h
function scanf()

I get a segmentation fault on execution after a successful compilation. What canbe going wrong here? I'm using Anjuta IDE 1.2.2 here.

```

#include<stdio.h>
//testfile...
int main() {
	int i=10,j=0;
            char a;
	printf("TestString...\n");
	printf("Hey enter the value of i here: ");
	scanf("%d", a);
	for (;j<=i;j++)
		printf("\n%d",j);
	printf("\nYou entered: %d", i);
	return 0;
}

```

Output:```

EXECUTING:
/home/nix/prog/test1
----------------------------------------------
TestString...
Hey enter the value of i here: 1

----------------------------------------------
Program has been terminated receiving signal 11 (Segmentation fault)
Press the Enter key to close this terminal ...

```

---

### Post by joft on 2006-02-07
[QUOTE=nixclusive]
```

#include<stdio.h>
//testfile...
int main() {
	int i=10,j=0;
            char a;
	printf("TestString...\n");
	printf("Hey enter the value of i here: ");
	scanf("%d", a);
	for (;j<=i;j++)
		printf("\n%d",j);
	printf("\nYou entered: %d", i);
	return 0;
}

```[/QUOTE]

You forget the fact that scanf needs pointers to the "return values". So use "scanf("%d", &a);". Otherwise scanf takes the (indefined) value of a as an address ... and thats causing the segfault.

---

### Post by nixclusive on 2006-02-07
Thanx, I'll return to Java ASAP!! I think I forgot quite a lot of C already :-

---

