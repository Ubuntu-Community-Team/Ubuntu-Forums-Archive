---
title: "Library missing - Where do I find it?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Shane11 on 2006-09-02
Another 'simple' question from a simple soul.

Still trying to install my Usb Belkin wireless thingy. (On Breezy.. Yes I know.....).

Here's the error.:confused: 

/usr/src/rt2570-1.1.0-b1/Module$ make
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!


Where do I get /lib/modules/2.6.12.10-386 from?

I've used Synaptic updates and this time I did the 'security' and 'updates' and ticked all the boxes. 
It went off and found me some new packages but still can't 'make' the rt2570 file.

Now I know there must be a little step that I've missed, maybe someone could point me in the right direction.8)

---

### Post by macdo on 2006-09-02
build-essentials, at a guess, isn't installed.
```
sudo apt-get install build-essential
```

HTH

EDIT: corrected command so that the package exists... (build-essential, not build-essential**s** :oops:

---

### Post by Shane11 on 2006-09-03
Hi and thanks but I have tried that apt-get install build-essentials.
That just tells me my system is up to date.

Any other ideas?

---

### Post by linuxa on 2006-09-03
Type this into the commandline:

sudo apt-get install linux-headers-`uname -r`

---

### Post by Shane11 on 2006-09-04
Hi Linuxa, thanks for that. That was exactly what I wanted. It's funny how frustrating Linux can be when you have tried every thing you can think of and some hero supplies another bit of the puzzle.

I'm sure i'll be back soon though:) There is always something new to learn. 

Can you explain what these linux-headers supply to the system? (in laymans terms preferably).

Regards
Shane.

---

### Post by Shane11 on 2006-09-04
Back sooner than I expected!
I got a tiny bit further there but no I get this error when I try to 'make' the file:

shane@ubuntushane:/usr/src/rt2570-1.1.0-b1/Module$ sudo make
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /usr/src/rt2570-1.1.0-b1/Module/rtusb_main.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/usr/src/rt2570-1.1.0-b1/Module/rtusb_main.o] Error 127
make[1]: *** [_module_/usr/src/rt2570-1.1.0-b1/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
rt2570.ko failed to build!
make: *** [module] Error 1

---

### Post by linuxa on 2006-09-09
**Shane**: The Linux headers are header declarations for the kernel source code. If you think of the Linux Kernel source code as pages in a book, the Headers are the Table of Contents for that book.

With regard to your second error, you need to install gcc-3.4, which is the GNU C Compiler version 3.4. To install it, type:

*sudo apt-get install gcc-3.4*

---

