---
title: "I get an error running MAKE"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-14
Hey, when I run the ./configure command on my package, it works fine...but hwen I run


sudo make, this is what I get : 

```

blah blah blah compiling but the screen cut it of.....etc etc


usbwrap.cc: In member function 'bool Usb::InterfaceDiscovery::Discover(Usb::usb_device*, int, int)':
usbwrap.cc:497: error: invalid use of undefined type 'struct Usb::usb_device'
usbwrap.h:67: error: forward declaration of 'struct Usb::usb_device'
usbwrap.cc:497: error: invalid use of undefined type 'struct Usb::usb_device'
usbwrap.h:67: error: forward declaration of 'struct Usb::usb_device'
usbwrap.cc:503: error: invalid use of undefined type 'struct Usb::usb_device'
usbwrap.h:67: error: forward declaration of 'struct Usb::usb_device'
usbwrap.cc: In member function 'bool Usb::ConfigDiscovery::Discover(Usb::usb_device*, int)':
usbwrap.cc:523: error: invalid use of undefined type 'struct Usb::usb_device'
usbwrap.h:67: error: forward declaration of 'struct Usb::usb_device'
usbwrap.cc:527: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:527: error: invalid use of undefined type 'struct Usb::usb_device'
usbwrap.h:67: error: forward declaration of 'struct Usb::usb_device'
usbwrap.cc:528: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:528: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:528: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:528: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:528: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:528: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:528: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:528: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:542: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:544: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:544: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:549: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:550: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:555: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc:556: error: 'struct Usb::ConfigDesc' has no member named 'desc'
usbwrap.cc: In member function 'bool Usb::DeviceDiscovery::Discover(Usb::usb_device*)':
usbwrap.cc:584: error: 'desc' was not declared in this scope
usbwrap.cc:584: error: invalid use of undefined type 'struct Usb::usb_device'
usbwrap.h:67: error: forward declaration of 'struct Usb::usb_device'
make[2]: *** [usbwrap.lo] Error 1
make[2]: Leaving directory `/home/b34st1y/Desktop/barry-0.11/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/b34st1y/Desktop/barry-0.11'
make: *** [all] Error 2
b34st1y@zer0cool:~/Desktop/barry-0.11$ 
```



what does it mean and how do I fix it ? ?

---

### Post by dstew on 2007-12-14
When you are compiling from source, you might need to have the correct headers installed. The compiler seems to be looking for definitions that are not there. You can install linux-headers appropriate to your kernel from Synaptic. You also have to be sure build-essential is installed. It seems like you have the latter since you have the compiler and make, but check in Synaptic to be sure.

---

### Post by B34ST1Y on 2007-12-15
what do you mean by headers? Which package do you think I need to install, if I'm trying to install a usb driver for my phone....running ubuntu gutsy 7.10

---

### Post by dstew on 2007-12-15
When compiling a program, the source code is converted to machine code by the compiler. However, usually the source code you download is incomplete. Even the starting "Hello world" program that we all learn is incomplete. In order for it to output data to the screen, it uses the printf function, which is not a part of the C language. The **printf** function is defined in a separate file, **stdio.h** which is included in the sources at compile time. These extra files are called "headers".

When a program is written for Linux, the bulk of the source code comes from headers. For example, the routines to access the disk, USB ports, printing, math functions and more are contained in header files that are part of the Linux source code. These header files need to be accessable to the compiler (that is, on your hard disk somewhere) at compile time. Most of the standard header files are installed with the **build-essential **package, but some programs need Linux-version specific headers.

With Ubuntu, almost all programs are compiled ahead of time, and downloaded and installed as binary (machine-readable) programs from the repositories. Synaptic is one of the graphical programs that let you do this. Since these are already compiled, you do not need the Linux headers to make them work. However, if you are compiling your program from source, and it needs some code from the headers, and they are not there, you will get errors. I think your errors are of this type.

That said, it might be that the program will not compile for other reasons. You could try to see if the source code supplier has any advice for you.

If you want to install the headers, the package name in Synaptic will be something like **linux-headers-2.6.20-15**. The numbers have to match your kernel version, which you can find using the command **uname -r**

---

### Post by B34ST1Y on 2007-12-15
crazy. it worked. thanks!! AHH!

---

