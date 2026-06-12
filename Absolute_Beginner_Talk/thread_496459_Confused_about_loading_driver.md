---
title: "Confused about loading driver"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Amplidude on 2007-07-09
Hi All

I've loaded Feisty (smooth as oiled silk, thank you) and  installed a GE-2032R  NIC which is seen as eth1. On the CD is a driver file, a "makefile" file and a readme (the makefile and readme are attached). 

I've read the Ubuntu documentation (compiling software, compiling easy how to) and the readme, but don't know how to proceed. Is it as simple as changing the Linux version number in the "NEW_INCLUDE_PATH" in make file and move commands and making the file? (how do I do that by the way, just type "sudo make" in the terminal?)

It all seems too easy, which means it probably is!  Please show me the way.

Thanks in advance

---

### Post by Vague on 2007-07-09
I might be missing something here, but if the card is already working, do you really need to install the drivers from the CD?

---

### Post by AlexenderReez on 2007-07-09
> **Amplidude said:**
> Hi All

I've loaded Feisty (smooth as oiled silk, thank you) and  installed a GE-2032R  NIC which is seen as eth1. On the CD is a driver file, a "makefile" file and a readme (the makefile and readme are attached). 

I've read the Ubuntu documentation (compiling software, compiling easy how to) and the readme, but don't know how to proceed. Is it as simple as changing the Linux version number in the "NEW_INCLUDE_PATH" in make file and move commands and making the file? (how do I do that by the way, just type "sudo make" in the terminal?)

It all seems too easy, which means it probably is!  Please show me the way.

Thanks in advance

extract and rename extract folder to driver .....copy extract folder....

then
> cd <paste here that copy folder>
make
sudo cp r8169.o /lib/modules/<**your kernel version**>/kernel/drivers/net
sudo insmod r8169.o
sudo dmesg ##just to check


---

### Post by Amplidude on 2007-07-09
> **Vague said:**
> I might be missing something here, but if the card is already working, do you really need to install the drivers from the CD?

Hi Vague
Sorry I was unclear. The card is "seen", but is not working. 
Ciao

---

### Post by Vague on 2007-07-09
> **Amplidude said:**
> Hi Vague
Sorry I was unclear. The card is "seen", but is not working. 
Ciao

Ahhh, sorry.  That makes sense now.

---

### Post by Amplidude on 2007-07-09
Thanks reez1015, I'll try that
Ciao

---

### Post by Amplidude on 2007-07-09
Oops. Something went wrong:

tony@Server1:~/Desktop/driver$ make
make: *** No rule to make target `/usr/include/linux/version.h', needed by `r8169.o'.  Stop.
tony@Server1:~/Desktop/driver$ 

I suspect I need to run the makefile code (see original post). How do I do this?

Thanks

---

### Post by AlexenderReez on 2007-07-09
> **Amplidude said:**
> Oops. Something went wrong:

tony@Server1:~/Desktop/driver$ make
make: *** No rule to make target `/usr/include/linux/version.h', needed by `r8169.o'.  Stop.
tony@Server1:~/Desktop/driver$ 

I suspect I need to run the makefile code (see original post). How do I do this?

Thanks

how about 

> ./Makefile 

---

### Post by Amplidude on 2007-07-09
Mmmm that didn't work either:

tony@Server1:~/Desktop/driver$ ./Makefile
: command not found 
./Makefile: line 4: MODCFLAGS: command not found
: No such file or directoryc/linux-2.6.20-16/include/
: command not found 
./Makefile: line 7: r8169.o:: command not found
./Makefile: line 8: CC: command not found
./Makefile: line 8: MODCFLAGS: command not found
./Makefile: line 8: NEW_INCLUDE_PATH: command not found
./Makefile: line 8: -c: command not found
: command not found 
: command not found: clean:
tony@Server1:~/Desktop/driver$ 

Any suggestions please?  Thanks

---

### Post by Rui Pais on 2007-07-09
Hi,
Do you realize that you are trying to install a version of 200**3** of r8169 for the olds 2.4 kernels?

Why don't you simply load the module from your Ubuntu kernel:
```
sudo modprobe r8169
``` 
?

---

### Post by Amplidude on 2007-07-09
Hi 

No, I didn't. I also didn't know that there was a module available in Ubuntu. I did the following:

tony@Server1:~$ sudo modprobe r8169
Password:
tony@Server1:~$ 

and the lack of error messages seems to imply that it worked.  I've checked the lib and it is there and I did a dmesg and it gave me screeds of output.  It works! Thank you. :)

---

### Post by Rui Pais on 2007-07-09
> **Amplidude said:**
> ... 
I did the following:

tony@Server1:~$ sudo modprobe r8169
Password:
tony@Server1:~$ 

and the lack of error messages seems to imply that it worked. 
yes, exactly :)

> 
 I've checked the lib and it is there and I did a dmesg and it gave me screeds of output.  It works!

You can use:
```
dmesg | tail
``` to show just the last logged thing things that happened

and, for checking if module is loaded you can do:
```
lsmod |grep r8169
```
or for more info:
```
lshw -C net
```

Now you probably would like that module loaded every time you boot. Do:
```
gksudo gedit /etc/modules
```

and add a line at the bottom of file with just:
```
r8169 
```

Glad i could help :)

---

### Post by Amplidude on 2007-07-11
Thank you! that worked.

---

