---
title: "Offline installations in Linux?"
date: 2013-08-04
forum: Any Other OS
---

### Post by andy_bay2 on 2013-08-04
Hi!

I'm trying to install the required software to get my Wifi to work on a g5 mac that has been converted to a Linux machine.

I found a tutorial (text below) that outlines this process, but the tutorial seems to assume the machine already has internet access. But I have no way of accessing internet with that computer before the WiFi starts working.

So my question is this: How should I change the code below if I have already transferred the necessary packages to my desktop (using a memory stick)? In other words, how do I tell the terminal to use existing files instead of trying to download something?

```

[LIST=1]
[*]Download, extract and build b43-fwcutter software version 011, which will be used to extract the Broadcom drivers:[INDENT]wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2 [ENTER]
tar xjf b43-fwcutter-011.tar.bz2 [ENTER]
cd b43-fwcutter-011 [ENTER]
make [ENTER]
[/INDENT]The make command above should generate output similar to the following:   cc -O2 -fomit-frame-pointer -std=c99 -Wall -pedantic -D_BSD_\
SOURCE-DFWCUTTER_VERSION_=006   -c -o fwcutter.o fwcutter.c
   cc -O2 -fomit-frame-pointer -std=c99 -Wall -pedantic -D_BSD_\
SOURCE-DFWCUTTER_VERSION_=006   -c -o md5.o md5.c
   cc -O2 -fomit-frame-pointer -std=c99 -Wall -pedantic -D_BSD_\
SOURCE-DFWCUTTER_VERSION_=006 -o bcm43xx-fwcutter fwcutter.o md5.o
... and you should be left with a binary executeable called *b43-fwcutter*.
[*]Type:[INDENT]cd .. [ENTER][/INDENT]
[*]Download and use fwcutter software to extract the Broadcom proprietary driver:[INDENT]wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2 [ENTER]
tar xjf broadcom-wl-4.150.10.5.tar.bz2 [ENTER]
b43-fwcutter-011/b43-fwcutter -w "/lib/firmware" broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o [ENTER]
[/INDENT]
[*]The b43 within the /lib/firmware directory should contain files:	[root@localhost ~]$ ll /lib/firmware/ [ENTER]
	a0g0bsinitvals4.fw
	a0g0bsinitvals5.fw
	a0g0bsinitvals9.fw
	a0g0initvals4.fw
	a0g0initvals5.fw
	a0g0initvals9.fw
	a0g1bsinitvals13.fw
	a0g1bsinitvals5.fw
	a0g1bsinitvals9.fw
	(more ...)
[/LIST]

```

---

### Post by GwL3eNC on 2013-08-04
Hi,

this is a bad tutorial, because which make command is meant. Whatever!!
If you have downloaded the files you first have to extract them. tar-bz2 is
a compressed archiv. I assume in there the source code of your device.
Normally there is an install instruction inside the folder (look at that!). Because the
text above talks about make i think it's a c++ programm. Nomrally such
code is build in three steps, but you must have installed

sudo apt-get install build-essential 

In most cases the codefiles contain a config file. In the first step you execute that with

./configfilename

then do a 

make 

and then a

sudo make install

Hope thats right for your project.

---

### Post by boast on 2013-08-04
looks like just the two wget lines should be ignored if you downloaded them on your stick already

just mount the usb stick, cd into the mounted usb location and then proceed with the tar extraction

---

### Post by wildmanne39 on 2013-08-04
There may be a better way please post the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by andy_bay2 on 2013-08-05
Hi!

Thanks to all for helping a noob like me!

Here's the output of the code you gave me:

[ATTACH=CONFIG]245079[/ATTACH]

---

### Post by Azdour on 2013-08-05
Hi,

I think you are going to need to specify which flavour of Linux you are using because looking at your screen-shot the lspci version you have is different to what I am seeing on Ubuntu, i.e it is complaining about not knowing the -k parameter which is missing from your lspci but not mine.  

Once you give Wild Man your version of Linux hopefully he can provide the correct command.

---

### Post by wildmanne39 on 2013-08-05
The command did not do what was expected, are you running redhat? if so I do not know anything about redhat, if not copy and pase the command for accuracy but it looks correct to me.

---

### Post by andy_bay2 on 2013-08-05
> **Wild Man said:**
> The command did not do what was expected, are you running redhat? if so I do not know anything about redhat, if not copy and pase the command for accuracy but it looks correct to me.

Hi!

I should have mentioned that the only Linux version I got to work with my power pc mac is called "Yellow Dog Linux".

I didn't think it would change the way offline installations would work, but in hindsight that was a erroneous assumption.

---

### Post by wildmanne39 on 2013-08-05
I am sorry that I can not help with this linux distribution, have you tried redhat forum?

---

### Post by wildmanne39 on 2013-08-05
*Thread moved to **Other OS/Distro Support**.*

---

