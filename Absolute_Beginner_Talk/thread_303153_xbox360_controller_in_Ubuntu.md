---
title: "xbox360 controller in Ubuntu"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2006-11-19
**Getting the Xbox360 Controller Working Edgy**

This guide is meant to be really easy; giving you reasons why you're doing things and explaining how to do them in simple language. Don't be afraid it almost impossible to mess up your system. READ the directions.


**You need to have automake1.9 & kernel-headers for your kernel**
```
sudo apt-get install linux-headers-'uname -r' build-essential
sudo apt-get install automake1.9

```

[B]
First you need to download two files:[/B]
Use these links (right click save as)
```
xpad.c
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c]("http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c")
xpad.h
-[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h]("http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h")
```


**Then your going to make a folder in your home directory called .xpad360 (the dot is to make it hidden)**
```
mkdir ~/.xpad360
```


**Now you are going to place the two files you downloaded (xpad.c & xpad.x) into the folder (.xpad360) you just created.**
1. Go to places->home
2. Once in your home folder either press Ctrl H (control key & h at the same time) or go to view-> show hidden files
3. Paste the two files you downloaded into the folder the folder you created, .xpad360

[B]
Now your going to make a Makefile:[/B]
```
gedit ~/.xpad360/Makefile
```

**And add this to that file and save:**
```
KERNEL_DIR?=/usr/src/linux-headers-2.6.17-10-generic

obj-m := xpad.o

EXTRA_CFLAGS= -I$(shell pwd)

all:
	$(MAKE) modules -C $(KERNEL_DIR) SUBDIRS=$(shell pwd)
```
*It is import that there is an indentation (Tab) before $(Make) in the above file. It will not work without it.
*Note the first line of the make file: **KERNEL_DIR?=/usr/src/linux-headers-2.6.17-10-generic** is my kernel and about 90% of everyone else's. If you followed all these steps and still can't get the file to make. You want to check your folder /usr/src/ and see what kernel your are using and amend the script accordingly.

[B]
Now your going to run the Makefile you just made:[/B] (YOUR NAME should be replaced with your login name)
```
cd /home/<YOUR NAME>/.xpad360
sudo make
```


**Now Your going to add the xpad360 "driver" into the /usb/inputs**
```
sudo cp xpad.ko /lib/modules/$(uname -r)/kernel/drivers/usb/input
```
[B]
Now to finish up:[/B]
```
sudo depmod -a
sudo modprobe xpad
```


**And to reboot:**
```
sudo shutdown -r now
```

Enjoy!

---

### Post by K.Mandla on 2006-11-19
Did you see the Xbox-Linux pages?

[http://www.xbox-linux.org/wiki/Main_Page](http://www.xbox-linux.org/wiki/Main_Page)

---

### Post by redDEADresolve on 2006-11-19
> **K.Mandla said:**
> Did you see the Xbox-Linux pages?

[http://www.xbox-linux.org/wiki/Main_Page](http://www.xbox-linux.org/wiki/Main_Page)

Thats for the Original Xbox, not for the Xbox360 controller. 

I want to be able to use my corded xbox360 usb controller in Ubuntu.

---

### Post by redDEADresolve on 2006-11-23
still nothing?

anyone got the xbox 360 controller working in edgy?

---

### Post by redDEADresolve on 2006-12-14
Thanks to po0f for catchin' those errors. I corrected them. And Muki for helping me to get this up and running.

---

### Post by po0f on 2006-12-14
redDEADresolve,

When creating the Makefile, you don't have to use sudo, as it's in your home directory.  And instead of typing out [FONT="Courier New"]gedit /home/<username>/.xpad360/Makefile[/FONT], you can shorten it to just [FONT="Courier New"]gedit ~/.xpad360/Makefile[/FONT].

Also, in your commands, you have home and username switched around, it should be /home/username, not /username/home.

And the command to install the driver would be [FONT="Courier New"]sudo **cp** ~/.xpad360/xpad.ko /lib/modules/`uname -r`/kernel/drivers/usb/input[/FONT] (you forgot the actual command.)  ;)

And a [FONT="Courier New"]depmod -a && modprobe xpad[/FONT] should be all you need to get it going, no reboot required.  :)

---

### Post by mukiex on 2006-12-14
Made a script for it, attached below.

It'll make the following folders :
~/my_driver/
~/my_drivers/xpad360/

Then it'll download both source files, build it, copy the module, and then apply it.


Note, you might need to install the following packages:

build-essential linux-headers(kernel_version)

(you would need to do this either way, whether using this script or the guide above)

You can get kernel_version with uname -r. Don't include the processor (386, K7 etc) when you go to download the headers.



So, super easy install guide :

1. save the txt file to your home folder.
2. Press Alt+F2 (run application) and type  :   xterm     ... hit enter ;)  ... in that box, type the following :
     a.     chmod +x xpad.txt
     b.     ./xpad.txt
3. Wait for it to finish ;)

---

### Post by zachstruck on 2006-12-17
Has anyone successfully gotten this to work on Feisty's new kernel?

---

### Post by mukiex on 2006-12-28
Hey guys. Script got updated. Hopefully it works now.

---

### Post by redDEADresolve on 2006-12-29
yeah the part that hanging people up trying to get it working in feisty or on an updated edgy kernel is when making the file, the fix is to direct it to the right version of your kernel.

go to
/usr/src/linux

and see what kernel you are using a send the make file command to the appropriate directory

---

### Post by redDEADresolve on 2007-01-13
The latest fix should reflect the kernel issue, please let me know if it works for you / give me feedback. Thanks.

---

### Post by proxess on 2007-02-24
I've been having this problem, with and without your script:

```
proxess@prxss:~$ ./xpad.txt 
Making Directories
Downloading Source
Warning: wildcards not supported in HTTP.
--00:10:06--  http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c
           => `xpad.c'
Resolving xbox-linux.cvs.sourceforge.net... 66.35.250.90
Connecting to xbox-linux.cvs.sourceforge.net|66.35.250.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]

    [ <=>                                                                                                                                     ] 18,863        --.--K/s             

00:10:07 (772.34 KB/s) - `xpad.c' saved [18863]

Warning: wildcards not supported in HTTP.
--00:10:07--  http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h
           => `xpad.h'
Resolving xbox-linux.cvs.sourceforge.net... 66.35.250.90
Connecting to xbox-linux.cvs.sourceforge.net|66.35.250.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]

    [ <=>                                                                                                                                     ] 4,381         --.--K/s             

00:10:07 (502.94 KB/s) - `xpad.h' saved [4381]

Building Makefile
Building Source... I'll need your password from here on
if you didn't run this as root
make modules -C /usr/src/linux-headers-2.6.20-8-generic  SUBDIRS=/home/proxess/my_drivers/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-8-generic'
  CC [M]  /home/proxess/my_drivers/xpad360/xpad.o
/home/proxess/my_drivers/xpad360/xpad.c: In function ‘xpad_process_packet’:
/home/proxess/my_drivers/xpad360/xpad.c:161: warning: implicit declaration of function ‘input_regs’
/home/proxess/my_drivers/xpad360/xpad.c: In function ‘xpad_probe’:
/home/proxess/my_drivers/xpad360/xpad.c:368: error: ‘SLAB_ATOMIC’ undeclared (first use in this function)
/home/proxess/my_drivers/xpad360/xpad.c:368: error: (Each undeclared identifier is reported only once
/home/proxess/my_drivers/xpad360/xpad.c:368: error: for each function it appears in.)
/home/proxess/my_drivers/xpad360/xpad.c:451: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
make[2]: *** [/home/proxess/my_drivers/xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/proxess/my_drivers/xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-8-generic'
make: *** [all] Error 2
Copying source...
cp: cannot stat `*.ko': No such file or directory
Apply source...
Done!
proxess@prxss:~$ 
```
;

I also tried:
in /usr/src/linux-headers-`uname -r`/includes/linux
-making a link of autoconf.h and call it config.h
-make a link of usb/input.h and call it usb_input.h

same problem;

And also tried modifying my xpad.c like shown  [HERE]("http://www.phoronix.net/forums/showthread.php?p=444")
again, same problem;

The problem is from building the source. Anyone have a solution?

Using Ubuntu Feisty 7.04 (Herd 4 i think it is, i keep my sys updated normaly).

Hope to be hearing from ya

---

### Post by po0f on 2007-02-24
proxess,

This tutorial won't work for Feisty kernels.  I've tried to build it myself and have gotten it to compile, but it doesn't work.  It looks like the maintainers of the xpad source have forgotten about it as they haven't updated it in a while.

---

### Post by redDEADresolve on 2007-02-24
poof is right my guide is for edgy, can work with dapper.

sorry that what happens when using bleeding edge software

---

### Post by MaX on 2007-03-19
Stolen from: [HOWTO_Xbox_360_cotnroller_on_Linux]("http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux")
Kernel prepared. Easy, no?

N.B.: The Xbox-Linux CVS driver does not currently work with kernels ==2.6.15. Use a lower kernel version until the driver is updated or use 2.6.16.

N.B.2: Kernel 2.6.18 changed the naming scheme for the usb-headers. To get the driver to compile under 2.6.18, you have to change

```
#include <linux/usb_input.h>
```

to
```
#include <linux/usb/input.h>
```

in xpad.c

N.B.3: To compile under kernel 2.6.19, just comment lines 54 and 161:
```
#include <linux/config.h>
```

to
```
/* #include <linux/config.h> */
```

and
```
input_regs(dev, regs);
```
to
```
/* input_regs(dev, regs); */
```


He's also a prepared xpad.c that fixes alot of other stuff but probably breaks original xbox controller support.
You can find that [here!]("http://home.presidenturkel.com/webfiles/xpad.c")

---

### Post by satore on 2007-03-26
I customized xpad.c for Xbox360 controller support under Feisty7.04(kernel 2.6.20)

[http://satore.ddo.jp/files/xpad360/xpad.c](http://satore.ddo.jp/files/xpad360/xpad.c)
[http://satore.ddo.jp/files/xpad360/xpad.h](http://satore.ddo.jp/files/xpad360/xpad.h)

My English is poor and do not expect the support of me, please.

---

### Post by redDEADresolve on 2007-03-27
thank you very much

---

### Post by zachstruck on 2007-04-09
Thank you everyone, especially for the 2.6.20 compatible files.  I can finally enjoy SNES games again.  This guide now works flawlessly with Feisty.

---

### Post by proxess on 2007-04-19
> **satore said:**
> I customized xpad.c for Xbox360 controller support under Feisty7.04(kernel 2.6.20)

[http://satore.ddo.jp/files/xpad360/xpad.c](http://satore.ddo.jp/files/xpad360/xpad.c)
[http://satore.ddo.jp/files/xpad360/xpad.h](http://satore.ddo.jp/files/xpad360/xpad.h)

My English is poor and do not expect the support of me, please.

thank you... can you make a diff file from the old version to the new? i'd like to see what you changed, seeing that i wasn't able to myself.


edit: im haveing a wee problem... my directional pad isnt working and the calibration of the analogs are way off...
is it also possible to get rumble??

---

### Post by proxess on 2008-05-02
Unfortunately this thread dies here. Hardy Kernel has xpad360 module in it. Goodbye!

---

### Post by cartisdm on 2008-05-02
> **proxess said:**
> Unfortunately this thread dies here. Hardy Kernel has xpad360 module in it. Goodbye!

Meaning it's just plug and play?

---

### Post by proxess on 2008-05-15
yep

---

