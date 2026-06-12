---
title: "Compiling Kernels? Headers?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by sbjaved on 2006-08-27
Hi from a noob...

I have navigated thru different posts for setting up things and they are always suggestting stuff like compiling Kernel and Installing essential Headers like it was as easy as chopping cabbage...

Would someone tell me what these headers are and what exactly do you mean by compiling kernel and what are the hazards if something goes wrong like you put an 'a' instead of 'b'?

Thanks.

P.S: Don't tell me to stick to Windows!

---

### Post by Klaidas on 2006-08-27
Well, if you compile your kernel wrong, you will still be able to go back to your original kernel and remove the wrongly compiled one.
It's not as easy as browsing the web, but it's not rocket science either :)

---

### Post by diepruis on 2006-08-27
Well... it's actually pretty complicated, but I'll try and explain.

The kernel is the core of any OS. Linux is different from Windows in that it can run many different kernels, specifically compiled for your hardware and needs. This type of kernel is called a monolithic kernel. Sometimes, you'll need to compile your own kernel to solve a problem, especially if it's a low level problem, like drivers or something.

Headers are simply files that describe functionality of a C / C++ program. The source code is the part that actually performs these functions. You need these headers to let programs you are compiling on your computer know what functions they can use and so on.

For example: Generally you can't use a driver compiled for a different kernel version. So if I have a driver for my wireless card that is compiled for a 386 kernel, I can't use it on my 686 kernel. I will have to compile the driver from source and install it on my 686 kernel. To do this, the program will use the 686 kernel headers to see what options were added and which removed when it was compiled. Usually, you don't have to do this, because Ubuntu's repositories come with many different versions of the kernel-dependant programs.

Clear enough?

---

### Post by moma on 2006-08-27
**Kernel headers:**
Kernel headers are C source code (*.h) files for the Linux kernel. These header files explain exactly what [COLOR="DarkRed"]structures[/COLOR] and [COLOR="DarkRed"]functions[/COLOR] the kernel has. So the headers are a link between external source code (you try to compile) and the Linux kernel itself. 

This command will install kernel-headers for your actual, running kernel:
What is the kernel version?
$ [COLOR="Green"]uname --kernel-release[/COLOR]

Install headers
$ [COLOR="Green"]sudo apt-get install linux-headers-$(uname -r)[/COLOR]

You can see the code in 
$ [COLOR="Green"]ls -l /lib/modules/$(uname -r)/build[/COLOR]
(it's a link to) 
$ [COLOR="Green"]ls -l /usr/src/linux-headers-$(uname -r)[/COLOR]

$ [COLOR="Green"]ls -l /usr/src[/COLOR]
----------------------

**Compilation of kernel:**
Get the kernel source from [http://www.kernel.org](http://www.kernel.org) or from Ubuntu's repositories.

[COLOR="DarkRed"]Configuration[/COLOR] and [COLOR="DarkRed"]compilation[/COLOR] of kernel is a pretty straightforward process. 

This is how I configured and compiled a new vanilla-kernel for Ubuntu.
[http://www.futuredesktop.org/kompilere_kjerne.html](http://www.futuredesktop.org/kompilere_kjerne.html)
The text is in Norwegian language, but you  will find important english language guides at the top of the page.

The preparation process will put new kernels into /boot/ directory. 
$ [COLOR="Green"]ls -l /boot[/COLOR] 

Kernel compilation in Ubuntu will also add new kernel titles to your GRUB boot-menu (/boot/grub/menu.lst).
$ [COLOR="Green"]cat /boot/grub/menu.lst[/COLOR]

All kernels use the same system files. System files DO NOT change even you compile and re-compile new kernels.  With system files I mean stuff in /usr/, /lib, /etc, /dev, /sys and /sbin.
----------------------

**What is "a vanilla kernel"?**
Vanilla kernel is a pure, unmodified kernel pulled from [http://www.kernel.org](http://www.kernel.org).  It's virgin and vanilla like vanilla ice cream.

RedHat, Ubuntu and certainly all major distro-vendors make some changes to the Linux kernel before they release their products. So they "pollute" the kernel with their own fixes and changes. IOW: the kernel is no longer "pure vanilla".

You can still get a vanilla kernel from [http://www.kernel.org](http://www.kernel.org), configure & compile it and it will work well in Ubuntu. No problem. It may lack some Ubuntu spesific enhancements, but it will run OK.

Kernel-source is normally saved in /usr/src directory. Kernel source is an huge pile (n * MB) of source code (both *.c and *,h files ) for the kernel and its drivers. If you already have the kernel-source then you will not need the kernel-headers (*.h files). Headers are included in the kernel-source.

In the kernel-source you will find a very important ".config" configuration file. It determines how the kernel is to be be compiled and what features and drivers it will include. 

Because these ".config" files are so important, Ubuntu saves'em in the /boot directory.

It's a good practice to grab one of these old, good .config files and copy it into new kernel-source (/usr/src/linux) directory. It will give you a good start.

$ [COLOR="Green"]ls -l /boot/config*[/COLOR]
-------------------------------------------------------------------

PS. Do not miss these links 
(Linux timeline, Linux kernel-reactor depicted etc.)
o--> [http://linux1.no/node/1934](http://linux1.no/node/1934)
;-)

---

