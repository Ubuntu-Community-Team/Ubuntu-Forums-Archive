---
title: "[SOLVED] whats the difference between using turboC and gcc"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Harish Prabhu on 2008-01-12
i wrote the following C code and tried to run it but its not even getting compiled

#include<stdio.h>
main ()
{char arr[6],int i;
for (i=0;i<4;i=i+1)
arr[i]='$';
arr[i]='/0';
for (i=0;i<4;i=i+1)
printf("element#%dis%c/n",i+1,arr[i]);
getch();
}

When i wrote the same code in TurboC,it works perfectly
why is it so?
Plealse help me

---

### Post by SOULRiDER on 2008-01-13
```

#include<stdio.h>
main ()
{
    char arr[6],int i;
    for (i=0;i<4;i=i+1)
        arr[i]='$';
    arr[i]='/0';
    for (i=0;i<4;i=i+1)
        printf("element#%dis%c/n",i+1,arr[i]);
    getch();
}

```

First of all, add the [code] tags, so the code stays indented.

Your main function has to return something, for the code to compile in gcc it will have to return an int. Im not sure about the getch() function.

You should post in the programming forum, more people will be able to help you there.

---

