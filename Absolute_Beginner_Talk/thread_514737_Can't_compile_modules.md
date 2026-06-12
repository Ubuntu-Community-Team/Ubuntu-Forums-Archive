---
title: "Can't compile modules"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Spippo on 2007-08-01
Hi all,

I'm trying to write a linux device driver as a module.
But I have a problem compiling this module. when I compile, I get the error:

**linux/module.h: no such file or directory**

I've looked for this error, and found that the modules aren't enabled during the installation, and that I don't have the linux headers.

So what i did was:

- download and install the linux headers : apt-get install linux-source-2.6.20
- extract the source (in /usr/src) : tar jxvf linux-source-2.6.20.tar.bz2
- copied the previous config: cp /boot/config-2.6.20-16-generic ./config
- config the new kernel : make menuconfig
- compiled the kernel modules : make modules

but still, i can't find module.h in /usr/include/linux
also, what options should I select in the menuconfig?

---

### Post by BobCFC on 2007-08-01
I have never written my own module, but I have compiled my own kernel a few times using advice from the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158").

In the /usr/src directory there are often many version of the source over time.  The convention is to have a symbolic link /usr/src/linux which points to the current version.

try 

```

cd /usr/src
ln -s /usr/src/linux-2.6.20 linux
```

Or whatever the directory of the source is called.

---

### Post by Spippo on 2007-08-01
I've created a symbolic link of the include directory from the source to the user include library, but now there are still other files it can't find.

I'm trying to compile this simple driver:
> 
#define __KERNEL__
#define MODULE
#include <linux/kernel.h>
#include <linux/module.h>


int init_module(void)
{
  printk(&#8220;Mijn module wordt geladen\n&#8221;);
}

void cleanup_modules(void)
{
  printk(&#8220;Mijn module wordt verwijderd\n&#8221;);
}


with this command :  **gcc test.c -o2 -c -o test.o**

Is there a certain package that need to be installed, that contains linux/module.h and those other headers?

---

### Post by BobCFC on 2007-08-01
I did not mean the include directory.  I mean a link at /usr/src/linux  which points to the current source directory.

I think you will find the path to include is probably set up to look for the headers relative to the /usr/src/linux sym link.

...
So the absolute location of your file might be

/usr/src/linux-2.6.20/include/linux/kernel.h

your compiler is set to look for header files with the path such as  /usr/src/linux/include, which is why you have the statement #include <linux/kernel.h>

therefore you need a symlink from /usr/src/linux which points to /usr/src/linux-2.6.20 or whichever tree you are using.

good luck!

---

