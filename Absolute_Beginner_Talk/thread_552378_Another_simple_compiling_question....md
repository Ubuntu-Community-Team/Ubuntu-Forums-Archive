---
title: "Another simple compiling question..."
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-09-16
Okay...I still learning new information everyday...

I was looking up some Apple mouse emulation for someone else on the forums (I don't have a mac). and I found a program called apple touch. So I downloaded the src and did exactly this:

```

isaac@isaac-laptop:~$ cd /home/isaac/Desktop/appletouch-0.08 
isaac@isaac-laptop:~/Desktop/appletouch-0.08$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/isaac/Desktop/appletouch-0.08 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/isaac/Desktop/appletouch-0.08/appletouch.o
/home/isaac/Desktop/appletouch-0.08/appletouch.c:28:26: error: linux/config.h: No such file or directory
/home/isaac/Desktop/appletouch-0.08/appletouch.c:36:29: error: linux/usb_input.h: No such file or directory
/home/isaac/Desktop/appletouch-0.08/appletouch.c: In function &#8216;atp_probe&#8217;:
/home/isaac/Desktop/appletouch-0.08/appletouch.c:369: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
/home/isaac/Desktop/appletouch-0.08/appletouch.c:371: warning: implicit declaration of function &#8216;init_input_dev&#8217;
/home/isaac/Desktop/appletouch-0.08/appletouch.c:373: error: &#8216;struct input_dev&#8217; has no member named &#8216;dev&#8217;
/home/isaac/Desktop/appletouch-0.08/appletouch.c:378: warning: implicit declaration of function &#8216;usb_to_input_id&#8217;
/home/isaac/Desktop/appletouch-0.08/appletouch.c: At top level:
/home/isaac/Desktop/appletouch-0.08/appletouch.c:449: error: unknown field &#8216;owner&#8217; specified in initializer
/home/isaac/Desktop/appletouch-0.08/appletouch.c:449: warning: initialization from incompatible pointer type
make[2]: *** [/home/isaac/Desktop/appletouch-0.08/appletouch.o] Error 1
make[1]: *** [_module_/home/isaac/Desktop/appletouch-0.08] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2
isaac@isaac-laptop:~/Desktop/appletouch-0.08$ 

```

Now I didn't do any "sudo make install" command as you can see. I'm just want to make sure I haven't changed anything on my laptop. This is just compiling in the folder correct?

**There are only 2 files in the folder apple-touch.c and makefile**

**I haven't change ANYTHING on my computer right (with the kernel and all that) or screwed anything up right?**

---

### Post by brennydoogles on 2007-09-16
> **isaacj87 said:**
> Okay...I still learning new information everyday...

I was looking up some Apple mouse emulation for someone else on the forums (I don't have a mac). and I found a program called apple touch. So I downloaded the src and did exactly this:

```

isaac@isaac-laptop:~$ cd /home/isaac/Desktop/appletouch-0.08 
isaac@isaac-laptop:~/Desktop/appletouch-0.08$ makemake -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/isaac/Desktop/appletouch-0.08 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/isaac/Desktop/appletouch-0.08/appletouch.o
/home/isaac/Desktop/appletouch-0.08/appletouch.c:28:26: error: linux/config.h: No such file or directory
/home/isaac/Desktop/appletouch-0.08/appletouch.c:36:29: error: linux/usb_input.h: No such file or directory
/home/isaac/Desktop/appletouch-0.08/appletouch.c: In function ‘atp_probe’:
/home/isaac/Desktop/appletouch-0.08/appletouch.c:369: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/isaac/Desktop/appletouch-0.08/appletouch.c:371: warning: implicit declaration of function ‘init_input_dev’
/home/isaac/Desktop/appletouch-0.08/appletouch.c:373: error: ‘struct input_dev’ has no member named ‘dev’
/home/isaac/Desktop/appletouch-0.08/appletouch.c:378: warning: implicit declaration of function ‘usb_to_input_id’
/home/isaac/Desktop/appletouch-0.08/appletouch.c: At top level:
/home/isaac/Desktop/appletouch-0.08/appletouch.c:449: error: unknown field ‘owner’ specified in initializer
/home/isaac/Desktop/appletouch-0.08/appletouch.c:449: warning: initialization from incompatible pointer type
make[2]: *** [/home/isaac/Desktop/appletouch-0.08/appletouch.o] Error 1
make[1]: *** [_module_/home/isaac/Desktop/appletouch-0.08] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2
isaac@isaac-laptop:~/Desktop/appletouch-0.08$ 

```

Now I didn't do any "sudo make install" command as you can see. I'm just want to make sure I haven't changed anything on my laptop. This is just compiling in the folder correct?

**There are only 2 files in the folder apple-touch.c and makefile**

**I haven't change ANYTHING on my computer right (with the kernel and all that) or screwed anything up right?**

Unless your configuration is strange, you can't cause any real problems without appending the command with sudo. With that said why the command ```
makemake -C
```??

shouldn't you just use ```
make
```?

---

### Post by schorsch on 2007-09-16
No, you didn't change anything on your computer when you you did not type "sudo make install". Calm down .. ;-) .... 
But a really better way to compile packages from sources and get a *.deb package afterwards which can can be extracted from the system is the use of "sudo checkinstall" instead of "sudo make install". The package "checkinstall" is in the repos and the installation is easy. You can even create a *.deb package without installing so that nothing can destroy something on your system!

BTW: Where did you get the sources from?

---

### Post by isaacj87 on 2007-09-16
It was just an error with the post...I corrected it! sorry...

---

### Post by isaacj87 on 2007-09-16
> **schorsch said:**
> No, you didn't change anything on your computer when you you did not type "sudo make install". Calm down .. ;-) .... 
But a really better way to compile packages from sources and get a *.deb package afterwards which can can be extracted from the system is the use of "sudo checkinstall" instead of "sudo make install". The package "checkinstall" is in the repos and the installation is easy. You can even create a *.deb package without installing so that nothing can destroy something on your system!

BTW: Where did you get the sources from?

[From here]("http://www.popies.net/atp/")

I was just doing research for a fellow Ubuntu user.

So with checkinstall...do I just run the command after "make"??

---

### Post by LKRaider on 2007-09-16
no, nothing was changed on your system, it just couldn't find some header files to compile the appletouch binary.

---

### Post by isaacj87 on 2007-09-16
> **LKRaider said:**
> no, nothing was changed on your system, it just couldn't find some header files to compile the appletouch binary.

Whew...nice...Glad I didn't wreck my system. Thanks for all the responses guys!!

---

### Post by schorsch on 2007-09-16
> **isaacj87 said:**
> [From here]("http://www.popies.net/atp/")

I was just doing research for a fellow Ubuntu user.

So with checkinstall...do I just run the command after "make"??

Yes, "sudo checkinstall" instead of "sudo make install" will build a deb-package and install it right away. If you just want to build the package "sudo checkinstall --install=no" will do the trick. This makes package maintenance much easier with software compiled from sources :-)

---

### Post by isaacj87 on 2007-09-16
> **schorsch said:**
> Yes, "sudo checkinstall" instead of "sudo make install" will build a deb-package and install it right away. If you just want to build the package "sudo checkinstall --install=no" will do the trick. This makes package maintenance much easier with software compiled from sources :-)

Wow...that would be easier! One question though, If I wanted to give other people the deb files it wouldn't work right? Because the dependencies wouldn't be set right? It would be pre-configured for me?

---

### Post by HermanAB on 2007-09-16
Hmm, maybe have a quick look at this guide:
[http://www.aeronetworks.ca/compile-howto.html](http://www.aeronetworks.ca/compile-howto.html)

Cheers,

H.

---

### Post by schorsch on 2007-09-16
> **isaacj87 said:**
> Wow...that would be easier! One question though, If I wanted to give other people the deb files it wouldn't work right? Because the dependencies wouldn't be set right? It would be pre-configured for me?
As long as other users have the same OS at the nearly same patch level I have never had any problems in the past .... :-)

---

### Post by schorsch on 2007-09-16
Uhm ... I just recognized the appletouch module is already available in the actual Feisty kernel ... ;-)

---

### Post by isaacj87 on 2007-09-16
Oh okay...I make sure to pass it on to the guy who needs it.

---

