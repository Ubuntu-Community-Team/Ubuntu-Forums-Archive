---
title: "usb wireless again!"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by marshaller on 2006-03-13
I found some drivers fore my wireless Zonet ZEW2501, but I dont know hav to install them. Here is what the instruction says.

Building zd1211:

------------



1)  untar the package using the command:

    tar zxvf zd1211-XXXX.tar.gz



2)  edit the Makefile to make sure the path of KERNEL_SOURCE is your

    are running, and the kernel version is correctly configure.

	

3)  Under zd1211-XXXX/zdsta directory, use "make clean", "make", "make install"

    to make and install driver.	


Can anyone explain it fore me.

---

### Post by Pragmatist on 2006-03-13
> 
 1)  untar the package using the command:
 
     tar zxvf zd1211-XXXX.tar.gz
 
 
 
 2)  edit the Makefile to make sure the path of KERNEL_SOURCE is your
 
     are running, and the kernel version is correctly configure.

Lets start with these two.  Have you downloaded the package?  If not, you need to download the zd1211-XXXX.tar.gz  the XXXX isn't part of the actual name, it is place of whatever is the current version number.  So download the most current copy of that file.  download it to your home directory.  and type the command given:
```
     tar zxvf zd1211-XXXX.tar.gz
```  Except in place of the XXXX put whatever the real numbers are.
Now you will have a new directory with a name very similar to the name of the file you downloaded.  Change into this new directory.  read the README and INSTALL files.  Then give us the output of this:
```
cat Makefile | grep KERNEL_SOURCE
```
and the output of this:
```
uname -r
```

---

### Post by marshaller on 2006-03-13
here are the output of the two

1.
KERNEL_SOURCE=/usr/src/linux-2.6.7
#KERNEL_SOURCE=/usr/src/linux-2.4.24
INCLUDES=-I$(KERNEL_SOURCE)/include -I$(SRC_DIR)/include/ -I$(SRC_DIR)
INCLUDES=-I$(KERNEL_SOURCE)/include -I$(SRC_DIR)/include/ -I$(SRC_DIR)
CFLAGS += -DMODVERSIONS -include $(KERNEL_SOURCE)/include/linux/modversions.h #kernel 2.4
2.
2.6.12-10-386

---

