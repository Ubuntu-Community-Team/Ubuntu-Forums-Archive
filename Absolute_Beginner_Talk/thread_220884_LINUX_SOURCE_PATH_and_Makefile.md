---
title: "LINUX_SOURCE_PATH and Makefile"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by emmettp on 2006-07-22
Hi,

I have just come over to Ubuntu 6.06 from Windows XP and I have to say well done to everybody involved, it is very, very good, particularily for the non-technical user. 

My substantive question is as follows. 

I am trying to get my iPAQ 4700x installed on the USB port and I find that I need to install an another package in addition to SynCE. So far so good. 

However when I try to run 'make' I get the message back that the program cannot find the linux_source_path specified in makefile and so cannot install the necessary drivers. 

The relevant lines from the makefile are:

LINUX_SOURCE_PATH := /usr/src/linux-$(shell uname -r)
KERNEL_BUILD_DIR := /lib/modules/$(shell uname -r)/build
USB_SERIAL_SOURCE_DIR := $(LINUX_SOURCE_PATH)/drivers/usb/serial

The makefile anticipates this possibility and advises in the comments to change the LINUX_SOURCE_PATH. However, I have searched the file tree and it is not obvious to me (almost certainly because I am new to Linux) what I should substitute for /usr/src/linux-$(shell uname -r) for the linux_source_path.

I'd appreciate any pointers as to the right reference.

Thanks in advance for any help.

Emmett

---

### Post by klytu on 2006-07-22
> **emmettp said:**
> Hi,

I have just come over to Ubuntu 6.06 from Windows XP and I have to say well done to everybody involved, it is very, very good, particularily for the non-technical user. 

My substantive question is as follows. 

I am trying to get my iPAQ 4700x installed on the USB port and I find that I need to install an another package in addition to SynCE. So far so good. 

However when I try to run 'make' I get the message back that the program cannot find the linux_source_path specified in makefile and so cannot install the necessary drivers. 

The relevant lines from the makefile are:

LINUX_SOURCE_PATH := /usr/src/linux-$(shell uname -r)
KERNEL_BUILD_DIR := /lib/modules/$(shell uname -r)/build
USB_SERIAL_SOURCE_DIR := $(LINUX_SOURCE_PATH)/drivers/usb/serial

The makefile anticipates this possibility and advises in the comments to change the LINUX_SOURCE_PATH. However, I have searched the file tree and it is not obvious to me (almost certainly because I am new to Linux) what I should substitute for /usr/src/linux-$(shell uname -r) for the linux_source_path.

I'd appreciate any pointers as to the right reference.

Thanks in advance for any help.

Emmett

It has been a while since I compiled anything from source, and I am sure some more experienced people will jump in and add to (or correct) this suggestion. Try typing (in a terminal window):

```
sudo apt-get install linux-headers-$(uname -r)
```

and then also:

```
sudo apt-get install build-essential
```

and post back if that helps.

---

### Post by emmettp on 2006-07-22
Thanks for the suggestion but I still get an error message: 

Can't find directory /usr/src/linux-2.6.15.26.386 
Edit /tmp/kernel-2.6-driver/Makefile and provide the correct source tree 
Make *** [/usr/src/linux-2.6.15.26.386] Error 1

Regards

Emmett

---

### Post by klytu on 2006-07-22
> **emmettp said:**
> Thanks for the suggestion but I still get an error message: 

Can't find directory /usr/src/linux-2.6.15.26.386 
Edit /tmp/kernel-2.6-driver/Makefile and provide the correct source tree 
Make *** [/usr/src/linux-2.6.15.26.386] Error 1

Regards

Emmett

OK. Looks like you might have to actually download kernel sources. I didn't think you would. This may help:

```
sudo apt-get install linux-source-$(uname -r)
```

---

