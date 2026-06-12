---
title: "how to run a C program in anjuta?"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by medya on 2006-04-22
hello I am learning C language , i used to use Turbo C in windows, I was told that I would need Anjuta in ubuntu so I installed it , now I want to test a simple C program that Adds two number . I type the source in a new file of Anjuta .

```
#include <stdio.h>
main ()
{
int a,b,sum;
scanf("%d %d",a,b);
sum=a+b;
printf("%d",sum);
getch();

}

```
now I want to test the program , how can I do that ? I want to give 4 and 3 to the program and recive 7 .

---

### Post by gondilon on 2006-04-22
go to the biuld menu and hit compile. If it compiles succefully, Go back to the menu and hit run. You might have to create a new project by going to file>new project. Good luck.

---

