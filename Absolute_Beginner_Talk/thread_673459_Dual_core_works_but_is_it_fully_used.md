---
title: "Dual core works but is it fully used?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by 3shirtlessmen on 2008-01-20
Hey everyone,

I've done my fair share of searching and I even read the threads that came up when I began typing this, although related, they are not really my question.

I am compiling some code (which the software is multi threaded) but the cores just change load every 2 seconds.. core 1 100% core 2 0%, core 1 0%, core 2 100% .. until it finishes compiling..

Now, shouldn't both cores be near max while compiling? If not, why?

Thanks

---

### Post by Nano Geek on 2008-01-20
Mine does that too. 
Probably the compiler is only set to use one core. Perhaps you can set it to use two but I don't know how.

---

### Post by tgalati4 on 2008-01-20
Try watching a video and compiling at the same time.  What does your load look like?
It's tough to parcel out compiling to two processors because of dependencies.  As new instructions are built, they require compatibility with what has already been built.  How do simultaneously build separate parts of the same application?

---

### Post by mitar on 2008-01-20
It can not be set for two since the programming languages (if we are talking about C, C++,...) are writen many years ago for processors that have only one core.

---

### Post by Rui Pais on 2008-01-20
> **mitar said:**
> It can not be set for two since the programming languages (if we are talking about C, C++,...) are writen many years ago for processors that have only one core.

You can use the fork() command to fork the processes and take advantage of the 2 processors:
```
#include <sys/types.h>
#include <unistd.h>
#include <iostream>

//teste fork() and speed

int main ( int argc ) {

  fork();

  long x,y;
  for(x = 0; x < 9999; x++)
    for(y = 0; y < 999999; y++);	
}
```

now if you compile and run normally it will use one core, but if you path argument 2 it will use the 2 cores.

---

### Post by oldb0y on 2008-01-20
> **mitar said:**
> It can not be set for two since the programming languages (if we are talking about C, C++,...) are writen many years ago for processors that have only one core.

+1
Dual-Core is a fairly new technology, and therefore not that many programs support multi-threading.

---

### Post by mitar on 2008-01-20
sorry, I forgot about this :-)

---

### Post by Hospadar on 2008-01-20
If you are talking about getting the compiler to compile using both cores, gcc doesn't do that automatically, there might be a flag to get it to do so however, you may want to look at the documentation.

If you are talking about writing a program that multithreads, you're going to have to use a library like libpthread or boost threads and spawn separate threads manually, and use mutex locks to keep them synchronized.

In general, linux does make full use of the cores, but if you have a program that only runs one process, there is no way for the OS to know how to safely break up the machine instructions to run them on both cores.  So unless a program explicitly spawns another thread to do work, it won't get run simultaneously on both cores.  However, if you have two big process running (like let's say ffmpeg and gcc) they will both run on a different core at the same time without you having to do anything.

If you are curious about exactly what is running where, you might want to use "htop" instead of the standard process manager, you can install htop with synaptic or apt-get.  htop gives you a more full view of all processes running, and shows the load on each core more clearly.

---

### Post by steveneddy on 2008-01-20
The processors should trade off, back and forth, until the compile is finished.

It works this way in my Gutsy 64 bit install.

---

