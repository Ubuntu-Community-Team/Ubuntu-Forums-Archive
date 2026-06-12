---
title: "wireless problems"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Tomas Galli on 2006-07-25
i have a nexxt usb wirelles adapter with a SIS163u chip. I trying to use Ndiswrapper having this error at "make" command 

mil000000@Yuku:~/ndiswrapper-1.21$ sudo make
make -C driver
make[1]: se ingresa al directorio `/home/mil000000/ndiswrapper-1.21/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: se sale del directorio `/home/mil000000/ndiswrapper-1.21/driver'
make: *** [all] Error 2


After check on many sources on the inetrnet i learn something about kernel issues and i did too many things, i can't remember exactly but 
I have the "build" directory (in /lib/modules/2.6.15-26-386) as a Symbolic link to the Linux-2.2.26 (in /usr/src)

It&#347; that ok?

Another thing:
This is what the computers say after "modinfo usbcore"
mil000000@Yuku:~/ndiswrapper-1.21$ modinfo usbcore 
filename:     /lib/modules/2.6.15-26-386/kernel/drivers/usb/core/usbcore.ko
license:        GPL
vermagic:       2.6.15-26-386 preempt 486 gcc-4.0
depends:
alias:          usb:v*p*d*dc09dsc*dp*ic*isc*ip*
alias:          usb:v*p*d*dc*dsc*dp*ic09isc*ip*
srcversion:     9665161864B20F4D8B8CCC2
parm:           usbfs_snoop:true to log all usbfs traffic (bool)
parm:           use_both_schemes:try the other device initialization scheme if the first one fails (bool)
parm:           old_scheme_first:start with the old device initialization scheme (bool)
parm:           blinkenlights:true to cycle leds on hubs (bool)
mil000000@Yuku:~/ndiswrapper-1.21$

and this after modprobe "ndiswrapper"

mil000000@Yuku:~/ndiswrapper-1.21$ modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
mil000000@Yuku:~/ndiswrapper-1.21$


HEEEEEEEELP

Totally Newbby

And sorry my english, i'm argenitne and is no enougth documentation and support in spanish

Thank&#347;

---

### Post by Dr. Nick on 2006-07-25
If you have wired internet access on the computer then I would bypass the make install bit and just install ndiswrapper-utils package from synaptic/apt-get. I think it is actually on the cd too incase you dont have internet.

To get make install to work you will probably need to install the kernel sources for your kernel, not exaclty sure what all it takes, Ive always used the prebuilt ver of ndiswrapper without issue

---

