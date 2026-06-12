---
title: "how to compile C program"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by harperd on 2006-09-25
I have downloaded from sourceforge the source for a program (rfswitch) to fix a specific WiFi problem with my Packard Bell laptop. I've got a file with extension C which I guess is the source code, also files called 'Makefile' and 'FILES'. There is also a Readme and licence file.

My problem is that I have no idea how to compile and install the program! I've checked the forums but I haven't managed to find any information I can understand.

I just need to know to do this and whether I need to install any other programs first.

Many Thanks

---

### Post by musab on 2006-09-25
> gcc -o file filename.c

or see whats inside the make file..I think you could just type

> make
or
> make all
or
>make install

---

### Post by croak77 on 2006-09-25
What does the README say.

---

### Post by harperd on 2006-09-26
Radio Kill Switch
------------ -----   -----       ----       ---       --         -
Most laptops provide the ability for the user to physically disable the radio.
Some vendors have implemented this as a physical switch that requires no
software to turn the radio off and on.  On other laptops, however, the switch
is controlled through a button being pressed and a software driver then making
calls to turn the radio off and on.  This is referred to as a "software based
RF kill switch"

Currently this project provides modules for controlling the software RF kill
switch on the Averatec 5100P and Packard Bell EasyNote E5.  The code may work
on other laptops, but these are the only models on which it has been tested.

To determine if you have a system that might be compatible with one of the
provided SW RF Kill switch modules, you can run:


        To check for the Packard Bell (to use module pbe) --

        % dd if=/dev/mem bs=1 skip=983040 count=65535 2>/dev/null | strings | egrep "NEW-PC|Insyde Software MobilePRO BIOS"

        To check for the Averatec (to use module av5100) --

        % dd if=/dev/mem bs=1 skip=983040 count=65535 2>/dev/null | strings | egrep "AVERATEC"

If you have one of those laptop models you can imply loading the av5100/pbe5
module and the radio will be toggled on and off.  In addition, you can turn
the driver on and off by writing either a 1 or 0 to /proc/av5100/radio or
/proc/pbe5/radio.  If you automatically load the av5100/pbe5 module when your
system boots, you may wish to use the radio module parameter to control the
state of the radio upon loading:

        modprobe av5100 radio=0
        modprobe pbe5 radio=0

results in the module loading with the radio turned off.  You can then turn the
radio on by:

        echo 1 > /proc/av5100/radio
        echo 1 > /proc/pbe5/radio

If you have a SW RF kill switch and can not use one of the above modules,
please join us on IRC (irc.freenode.net) on channel #ipw2100 and someone may
be able to help.

---

### Post by harperd on 2006-09-26
This is the Make file

#
# Makefile for the SW RF Switch kernel modules
#
# NOTE: This make file can serve as both an external Makefile (launched
#       directly by the user), or as the sub-dir Makefile used by the kernel
# 	build system.


CONFIG_AVERATEC_5100P=m
CONFIG_PACKARDBELL_E5=m



list-m :=
list-$(CONFIG_AVERATEC_5100P) += av5100
list-$(CONFIG_PACKARDBELL_E5) += pbe5


obj-$(CONFIG_AVERATEC_5100P) += av5100.o
obj-$(CONFIG_PACKARDBELL_E5) += pbe5.o

#
# Begin dual Makefile mode here.  First we provide support for when we
# are being invoked by the kernel build system
#
ifneq ($(KERNELRELEASE),)

ifneq ($(PATCHLEVEL),6) # If we are not on a 2.6, then do 2.4 specific things

O_TARGET := rfswitch.o

include $(TOPDIR)/Rules.make

endif # End if 2.4 specific settings

else 
# Here we begin the portion that is executed if the user invoked this Makefile
# directly.

# KSRC should be set to the path to your sources
# modules are installed into KMISC
KVER  := $(shell uname -r)
KSRC := /lib/modules/$(KVER)/build
KMISC := /lib/modules/$(KVER)/kernel/drivers/net/wireless/

# KSRC_OUTPUT should be overridden if you are using a 2.6 kernel that
# has it's output sent elsewhere via KBUILD_OUTPUT= or O=
KSRC_OUTPUT := $(KSRC)

# If we find Rules.make, we can assume we're using the old 2.4 style building
OLDMAKE=$(wildcard $(KSRC)/Rules.make)
PWD=$(shell pwd)

VERFILE := $(KSRC_OUTPUT)/include/linux/version.h
KERNELRELEASE := $(shell \
	if [ -r $(VERFILE) ]; then \
		(cat $(VERFILE); echo UTS_RELEASE) | \
		$(CC) -I$(KSRC_OUTPUT) $(CFLAGS) -E - | \
		tail -n 1 | \
		xargs echo; \
        else \
		uname -r; \
	fi)

MODPATH := $(DESTDIR)/lib/modules/$(KERNELRELEASE)

all: modules

clean:
	rm -f *.mod.c *.mod *.o *.ko .*.cmd .*.flags Modules.symvers
	rm -rf $(PWD)/tmp


ifeq ($(OLDMAKE),)

TMP=$(PWD)/tmp
MODVERDIR=$(TMP)/.tmp_versions

modules:
ifdef ($(KSRC_OUTPUT)/.tmp_versions)
	mkdir -p $(MODVERDIR)
	-cp $(KSRC_OUTPUT)/.tmp_versions/*.mod $(MODVERDIR)
endif
ifeq ($(KSRC),$(KSRC_OUTPUT)) # We're not outputting elsewhere
ifdef ($(KSRC)/.tmp_versions)
	-cp $(KSRC)/.tmp_versions/*.mod $(MODVERDIR)
endif
	$(MAKE) -C $(KSRC) SUBDIRS=$(PWD) MODVERDIR=$(MODVERDIR) modules
else # We've got a kernel with seperate output, copy the config, and use O=
	mkdir -p $(TMP)
	cp $(KSRC_OUTPUT)/.config $(TMP)
	$(MAKE) -C $(KSRC) SUBDIRS=$(PWD) MODVERDIR=$(MODVERDIR) O=$(PWD)/tmp modules
endif

install: modules
	install -d $(KMISC)
	install -m 644 -c $(addsuffix .ko,$(list-m)) $(KMISC)
	/sbin/depmod -a


else # We're on 2.4, and things are slightly different

modules:
	$(MAKE) -C $(KSRC) SUBDIRS=$(PWD) BUILD_DIR=$(PWD) modules

install: modules
	install -d $(KMISC)
	install -m 644 -c $(addsuffix .o,$(list-m)) $(KMISC)
	/sbin/depmod -a

endif

uninstall:
	rm -rf $(KMISC)
	/sbin/depmod -a

endif

---

### Post by harperd on 2006-09-26
got this when I tried to compile

david@10:~/temp/rfswitch-1.1$ gcc -o file pbe5.c
In file included from pbe5.c:28:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read
 the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at [http://ep09.pld](http://ep09.pld)
-linux.org/~mmazur/linux-libc-headers/doc/)"
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from pbe5.c:31:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h
>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from pbe5.c:31:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from pbe5.c:31:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
In file included from pbe5.c:35:
/usr/include/linux/proc_fs.h:4:24: error: linux/slab.h: No such file or director
y
In file included from pbe5.c:35:
/usr/include/linux/proc_fs.h:245: error: field ‘vfs_inode’ has incomplete type
/usr/include/linux/proc_fs.h: In function ‘PROC_I’:
/usr/include/linux/proc_fs.h:250: error: syntax error before ‘struct’
pbe5.c:37:25: error: asm/uaccess.h: No such file or directory
In file included from /usr/include/asm/io.h:11,
                 from pbe5.c:38:
/usr/include/asm-i386/io.h:1:2: warning: #warning "You should include <sys/io.h>
. This time I will do it for you."
pbe5.c: In function ‘pbe5_get_radio’:
pbe5.c:87: error: ‘KERN_INFO’ undeclared (first use in this function)
pbe5.c:87: error: (Each undeclared identifier is reported only once
pbe5.c:87: error: for each function it appears in.)
pbe5.c:87: error: syntax error before string constant
pbe5.c: In function ‘pbe5_set_radio’:
pbe5.c:104: error: ‘KERN_INFO’ undeclared (first use in this function)
pbe5.c:104: error: syntax error before string constant
pbe5.c:115: error: syntax error before string constant
pbe5.c:118: error: syntax error before string constant
pbe5.c: At top level:
pbe5.c:130: warning: ‘struct file’ declared inside parameter list
pbe5.c: In function ‘proc_get_radio’:
pbe5.c:142: warning: incompatible implicit declaration of built-in function ‘snp                                          rintf’
pbe5.c: In function ‘pbe5_proc_init’:
pbe5.c:165: error: ‘S_IFDIR’ undeclared (first use in this function)
pbe5.c:168: error: ‘KERN_ERR’ undeclared (first use in this function)
pbe5.c:168: error: syntax error before string constant
pbe5.c:174: error: ‘S_IFREG’ undeclared (first use in this function)
pbe5.c:174: error: ‘S_IRUGO’ undeclared (first use in this function)
pbe5.c:174: error: ‘S_IWUSR’ undeclared (first use in this function)
pbe5.c:178: warning: assignment from incompatible pointer type
pbe5.c:181: error: syntax error before string constant
david@10:~/temp/rfswitch-1.1$

---

