---
title: "Hello Kernel =)"
date: 2008-06-04
forum: Beginner Team
---

### Post by makyramallo_22 on 2008-06-04
Hi! 
 I just wanted to create a very simple kernel module, here is the code:

#include <linux/module.h>


int minit_module(void)
{
      printk("Hello kernel\n");
        return 0;

}

void mcleanup_module(void)
{
      printk("Bye kernel\n");
}

module_init(minit_module);
module_exit(mcleanup_module);
MODULE_LICENSE("GPL");

The problem is that when I compile it using:

$ gcc -o test test.c

It can't find the linux/module.h so I can't run it. =S

Thanks for your help! =)

---

### Post by Thanoulis on 2008-06-04
My module.h is in: /usr/src/linux-headers-2.6.24-18/include/linux/module.h
Try to find where is yours, and include the whole path...(just a thought though, i do not know a thing about kernel module building...)

---

### Post by wdaniels on 2008-06-04
The error is because you didn't tell gcc where to look for the kernel headers. But for compiling kernel modules there are other things that really need to be taken into account and you really need to use a makefile otherwise it gets a bit complicated. A simple makefile example for this would be:

```
obj-m += test.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

Create this file as "Makefile" in the same directory as test.c and then run "make". You should get a file test.ko which you can then load into the kernel with:

```
sudo insmod test.ko
```

You should then see your message in the system log. Remove using rmmod.

---

### Post by wdaniels on 2008-06-05
Of course, you need to actually install the kernel headers first - you did that already right? If not:

```
sudo apt-get install linux-headers-generic
```

(assuming it's the generic kernel you're using)

---

