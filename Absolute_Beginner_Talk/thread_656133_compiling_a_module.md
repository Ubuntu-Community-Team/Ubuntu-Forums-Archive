---
title: "compiling a module"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by redscorpion07 on 2008-01-02
i want to compile a module and when i type this:
```

make -C /lib/modules/2.6.20-16-generic/build M=`pwd` modules

```
 
i got this error:
```

root@msc:/home/sercan/Desktop/drivers# make -C /lib/modules/2.6.20-16-generic/build M=`pwd` modules
make: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/sercan/Desktop/drivers/scull.o
/home/sercan/Desktop/drivers/scull.c:1:26: error: linux/config.h: No such file or directory
make[1]: *** [/home/sercan/Desktop/drivers/scull.o] Error 1
make: *** [_module_/home/sercan/Desktop/drivers] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'


```

i am a newer user so i am sorry if this is a easy problem to ask

---

### Post by kevdog on 2008-01-02
What exactly are you trying to compile?

It seems like you know this already, but its usually
./configure
make 
sudo make install

Your command line option is different (which may be the case for you).

---

### Post by sailor2001 on 2008-01-02
install build-essentials (synaptics) first

---

### Post by redscorpion07 on 2008-01-02
> **sailor2001 said:**
> install build-essentials (synaptics) first

i had done it but there is no change

---

### Post by redscorpion07 on 2008-01-02
> **kevdog said:**
> What exactly are you trying to compile?

It seems like you know this already, but its usually
./configure
make 
sudo make install

Your command line option is different (which may be the case for you).

actually i am a student and this is a driver which is a project of a course of mine
 you mentioned that 
./configure 
make
sudo make install

where should i do these i mean in which directory

---

### Post by kevdog on 2008-01-02
Change into the top level directory where the sources are located.  Look for a configure or autogen.sh file.  Is there one listed?   If not how about a README or INSTALL text file that you can read that might give instructions.

---

### Post by redscorpion07 on 2008-01-02
i had solved this problem with changing the ```
#include <linux/config.h>
``` to ```
#include <linux/autocnf.h
```

thanks for help

---

