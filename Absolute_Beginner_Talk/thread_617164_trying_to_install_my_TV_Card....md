---
title: "trying to install my TV Card..."
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by benjamin222 on 2007-11-19
Hey.. Feel like I'm almost all the way there with the TV card.. still not working though. It's a Nogatech USB, I found a website explaining how to get it set up...

[http://usbvision.sourceforge.net/index.php?page=documentation](http://usbvision.sourceforge.net/index.php?page=documentation)

anyway, I downloaded the usbvision-0.9.8.3 drivers there, and I'm reading the website, which says...


------------------------------
"There are two ways to do this. For both you must have installed the kernel sources. The files
    /lib/modules/kernel_version/build/.config    and 
    /lib/modules/kernel_version/build/linux/version.h 
have to reflect the running kernel.
On most standard installations the current configuration file is
    /boot/kernelname.config    and the version-file is
    /boot/kernelname.version.h
Copy this files if needed.


First way (The easy one)
---------

It works with most modern standard installations.

a) In the usbvision directory do
   make; make install; make modprobe

b) Start your video application.

c) Enjoy.

If c) doesn't work, something went wrong ;-)"

---------------------------------

and the 2nd way to do it is pretty long and confusing, not to mention its telling me to look at and put files into folders that don't exist.

Soooo anywhoo I entered make and here is what I got...

benjamin@benjamin:~/Desktop/usbvision-0.9.8.3/usbvision/src$ make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/benjamin/Desktop/usbvision-0.9.8.3/usbvision/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/benjamin/Desktop/usbvision-0.9.8.3/usbvision/src/i2c-algo-usb.o
/home/benjamin/Desktop/usbvision-0.9.8.3/usbvision/src/i2c-algo-usb.c:45: error: expected ‘)’ before string constant
/home/benjamin/Desktop/usbvision-0.9.8.3/usbvision/src/i2c-algo-usb.c:219: error: unknown field ‘slave_send’ specified in initializer
/home/benjamin/Desktop/usbvision-0.9.8.3/usbvision/src/i2c-algo-usb.c:220: error: unknown field ‘slave_recv’ specified in initializer
make[2]: *** [/home/benjamin/Desktop/usbvision-0.9.8.3/usbvision/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/home/benjamin/Desktop/usbvision-0.9.8.3/usbvision/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
benjamin@benjamin:~/Desktop/usbvision-0.9.8.3/usbvision/src$



yeah... bunch of error messages.. so if anyone can help me out with installing this would be greatly appreciated times a million!!! Oh yeah, and I'm not sure if I have the kernel sources, how could I go about finding that out / getting them?

---

