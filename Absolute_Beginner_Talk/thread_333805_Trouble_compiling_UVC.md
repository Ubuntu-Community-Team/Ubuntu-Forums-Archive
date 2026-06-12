---
title: "Trouble compiling UVC"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Chonnawonga on 2007-01-07
I'm pretty new to Ubuntu and still trying to figure things out.

In trying to compile the UVC driver in Edgy for my Logitech Quickcam Pro 5000, I get the following error:

brad@Limetop:~/uvcdriver$ make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[2]: *** No rule to make target `/home/brad/uvcdriver/uvc_driver.o', needed by `/home/brad/uvcdriver/uvcvideo.o'.  Stop.
make[1]: *** [_module_/home/brad/uvcdriver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [uvcvideo] Error 2


Here is the "Makefile":
KERNEL_VERSION	:= `uname -r`
KERNEL_DIR	:= /lib/modules/$(KERNEL_VERSION)/build
INSTALL_MOD_DIR	:= usb/media

PWD		:= $(shell pwd)

obj-m		:= uvcvideo.o
uvcvideo-objs   := uvc_driver.o uvc_queue.o uvc_v4l2.o uvc_video.o uvc_ctrl.o

all: uvcvideo

uvcvideo:
	@echo "Building USB Video Class driver..."
	@(cd $(KERNEL_DIR) && make -C $(KERNEL_DIR) SUBDIRS=$(PWD) modules)

install:
	@echo "Installing USB Video Class driver..."
	@(cd $(KERNEL_DIR) && make -C $(KERNEL_DIR) SUBDIRS=$(PWD) INSTALL_MOD_DIR=$(INSTALL_MOD_DIR) modules_install)
	depmod -ae

clean:
	-rm -f *.o *.ko .*.cmd .*.flags *.mod.c Modules.symvers
	-rm -rf .tmp_versions


Can anybody tell me what I'm missing here?

Thanks!

---

### Post by ajmorris on 2007-01-07
is there a configure script there? That should be run first.

---

### Post by Chonnawonga on 2007-01-07
Hi ajmorris,

I don't think there's a configuration script, no.

These are the files I have in this directory:

Makefile       uvc_ctrl.c   uvc_v4l2.c   uvcvideo.h
uvc_compat.h  uvc_queue.c  uvc_video.c

...which I downloaded from [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/)

Is there somewhere else I might find a config script?

---

### Post by r.stiltskin on 2007-01-08
You seem to be missing uvc_driver.c

---

### Post by Chonnawonga on 2007-01-08
> **r.stiltskin said:**
> You seem to be missing uvc_driver.c

Thank you, r.stiltskin! If you'll excuse me, I'm going to go smack myself now.

(If anyone's wondering, it compiles and installs perfectly now.)

---

