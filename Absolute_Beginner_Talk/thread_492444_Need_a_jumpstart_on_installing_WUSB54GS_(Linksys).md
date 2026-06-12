---
title: "Need a jumpstart on installing WUSB54GS (Linksys)"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by hardysmiles on 2007-07-04
I have read the HOWTO: WUSB54GS tutorial, which is great, but I am really new at this and need some help with the first step (and a few other steps). They are pretty basic, so if someone could spell some stuff out for me and help me get going, I would be really greatful.

Step 1 is Installing the Essentiels. You' re supposed to type the following in the terminal:

sudo apt-get install cpp gcc build-essential linux-headers-$ (uname -r)

which i did and i got:

reading package lists...done
building dependency tree
reading state info...done
cpp is already newest version
gcc is already newest version
E: couldn' t find package build-essentiel

What does this last line mean? Was I supposed to modify that command, for example adding the path to something in the attachment that the tutorial-author has provided?

I have other questions, but I'd rather wait until I get to those steps in hope things will become clearer and I'll figure it out. Thanks for your help

-hilary.

---

### Post by JawsThemeSwimming428 on 2007-07-04
You aren't supposed to have the dollar sign ($) after the linux-headers part (I don't think). Also, you replaced (uname -r) with your user name correct? gcc and cpp are both the most current version so try to run the command with just build essentials. If that doesn't work did you try getting it from Synaptic?

---

### Post by hardysmiles on 2007-07-04
Thanks for replying :-),

allright so I have learned that you're supposed to type the command line as is, without any space between the $ and (uname -r)

also i double checked by just doing uname -r to see what linux-header already's on my computer and the output was 2.6.20-15-generic so I went on to step two (also realizing the apt-get wont work since the computer i'm working on doesn't have internet right now).

I've gone on to Step 2 :p and am getting error messages...
This step is building the ndiswrapper. Here's what i'm supposed to do: extract folders from attachment from the tutorial, then go into the ndiswrapper folder in the terminal and run:
sudo make uninstall
make
sudo make install

He mentioned that some have the error message about directories unable to be deleted so he suggests the command:
sudo rm -fR /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper

Then finish it off with
sudo ndiswrapper -m

Here's what went on in my terminal:

hilary@hilary:~$ cd /home/hilary/ndiswrapper-files/ndiswrapper-1.28
hilary@hilary:~/ndiswrapper-files/ndiswrapper-1.28$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper': Is a directory
make: *** [uninstall] Error 1
hilary@hilary:~/ndiswrapper-files/ndiswrapper-1.28$ sudo rm -fR lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper
hilary@hilary:~/ndiswrapper-files/ndiswrapper-1.28$ sudo make
make -C driver
make[1]: Entering directory `/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M] /home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.o
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c:39:47: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c: In function â&#8364;&#732;ndis_initâ&#8364;&#8482;:
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c:39: error: â&#8364;&#732;INIT_WORKâ&#8364;&#8482; undeclared (first use in this function)
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c:39: error: (Each undeclared identifier is reported only once
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c:39: error: for each function it appears in.)
make[3]: *** [/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.o] Error 1
make[2]: *** [_module_/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver'
make: *** [all] Error 2
hilary@hilary:~/ndiswrapper-files/ndiswrapper-1.28$ sudo make install
make -C driver install
make[1]: Entering directory `/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M] /home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.o
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c:39:47: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c: In function â&#8364;&#732;ndis_initâ&#8364;&#8482;:
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c:39: error: â&#8364;&#732;INIT_WORKâ&#8364;&#8482; undeclared (first use in this function)
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c:39: error: (Each undeclared identifier is reported only once
/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.c:39: error: for each function it appears in.)
make[3]: *** [/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver/ndis.o] Error 1
make[2]: *** [_module_/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/hilary/ndiswrapper-files/ndiswrapper-1.28/driver'
make: *** [install] Error 2
hilary@hilary:~/ndiswrapper-files/ndiswrapper-1.28$ sudo ndiswrapper -m
sudo: ndiswrapper: command not found
hilary@hilary:~/ndiswrapper-files/ndiswrapper-1.28$


Why the error messages?
What can I do?

---

### Post by javaJake on 2007-07-07
This question is being answered here:
[https://answers.launchpad.net/ubuntu/+question/9235](https://answers.launchpad.net/ubuntu/+question/9235)

Any discussion should continue there.

---

