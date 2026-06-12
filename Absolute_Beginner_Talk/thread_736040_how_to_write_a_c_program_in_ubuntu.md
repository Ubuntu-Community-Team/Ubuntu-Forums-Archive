---
title: "how to write a c program in ubuntu"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by 7raTEYdCql on 2008-03-26
can someone give me a step by step procedure of how to write a c program in ubuntu.

---

### Post by pseudo-random on 2008-03-26
using a text editor write this:
> #include <stdio.h>

int main ()
{
  printf ("Hello World!\n");
}
save it as hello.c
Then from a command line compile it with:
gcc -o hello  hello.c
Make it executable:
chmod a+x hello
then run it:
./hello

---

### Post by 7raTEYdCql on 2008-03-26
In reply to what you just posted.

what does chmod do and what does that command line actually mean.

thanking you.

---

### Post by Junglizer on 2008-03-26
Chmod changes file permissions. He is showing you how to make it an executable file, so that you can run it using the ./ opperation.

[http://www.linuxmanpages.com/man1/chmod.1.php]("http://www.linuxmanpages.com/man1/chmod.1.php")

chmod a+x hello

change permissions of file 'hello' to be executable (x) by all users (a).

---

### Post by mali2297 on 2008-03-26
I don't think you need to use chmod, the file will be executable anyhow.

You reach the *command line* by opening **Applications menu -> Accessories -> Terminal**.
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Also, to get the C compiler and other things, you need to install **build-essential**.
```

sudo apt-get install build-essential

```

---

