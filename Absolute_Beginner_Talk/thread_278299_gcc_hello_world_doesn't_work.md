---
title: "gcc hello world doesn't work"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by todos on 2006-10-16
Hi, I'm trying to learn how to program in C. I copied a hello world file and tried to run it in gcc but doesn't run.

Can anyone help me?

This is my code:

#include <stdio.h>

int main() {
printf("Hello World") ;
getchar();
return 0;
}

And this is what I get when I type:
~$ gcc helloworld.c

helloworld.c:1:19: error: stdio.h: No such file or directory
helloworld.c: In function 'main':
helloworld.c:4: warning: incompatible implicit declaration of built-in function 'printf'

Can anyone help me please? What I'm doing wrong and I would like to know if I'm missing anything.

Regards,

Juan.-

---

### Post by dmizer on 2006-10-16
looks like you've forgotten a ; after int main() ... ?

---

### Post by mostwanted on 2006-10-16
```
sudo apt-get install build-essential
```

---

### Post by todos on 2006-10-16
dmizer, mostwanted thanks I will try it :)

---

