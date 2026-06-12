---
title: "Makefiles"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Gummi_ellahi on 2007-02-18
im trying to install my belkin wireless card and have downloaded the rt2500 driver but it contains a makefile. i have unpacked it onto my desktop. where and how do i compile the makefile? any tips gratefully accepted.

---

### Post by Perfect Storm on 2007-02-18
A good idea will be to read the readme.txt first (if it contains one) or read if there's any instruction/comment from the people who made. Then;
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential
cd <into the extracted driver folder>
make
sudo make install
```


(it properly needs kernel headers aswell)

---

### Post by Gummi_ellahi on 2007-02-18
kernel headers? sorry i'm REALLY new to linux

---

### Post by Perfect Storm on 2007-02-18
ah, sorry. Forgetting sometimes, my fault.


```
sudo aptitude install linux-headers-`uname -r`
```

---

### Post by Gummi_ellahi on 2007-02-18
amir@amir-laptop:~$ cd /home/amir/Desktop/rt2500/Module/2.6.x
amir@amir-laptop:~/Desktop/rt2500/Module/2.6.x$ make
rm -f *.o *~ .*.cmd *.ko *.mod.c
amir@amir-laptop:~/Desktop/rt2500/Module/2.6.x$ sudo make install
make: *** No rule to make target `install'.  Stop.
amir@amir-laptop:~/Desktop/rt2500/Module/2.6.x$ cd /home/amir/Desktop/rt2500/Module
amir@amir-laptop:~/Desktop/rt2500/Module$ make
Makefile:5: config.mk: No such file or directory
make: *** No rule to make target `config.mk'.  Stop.
amir@amir-laptop:~/Desktop/rt2500/Module$ makefile
bash: makefile: command not found
amir@amir-laptop:~/Desktop/rt2500/Module$ 

problems? please help im starting to get really frustrated!:confused:

---

### Post by lamego on 2007-02-18
Have you checked the readme ?
Eventually the source comes with a "configure" script, you need to run "./configure" to generate the make files previous to rung "make".

---

### Post by Perfect Storm on 2007-02-18
Perhaps someone else can help, as I have no experience with wireless cards.
But might take a look at this : [http://doc.gwos.org/index.php/Ralink_RT2570_usb_wireless_driver](http://doc.gwos.org/index.php/Ralink_RT2570_usb_wireless_driver) though it isn't your card, try with the same proceedor.

---

### Post by Gummi_ellahi on 2007-02-18
a.  $make -C /path/to/source SUBDIRS=$PWD modules
    Where /path/to/source is the path to the source directory for the (configured and built) target kernel.

b.  run '/sbin/insmod rt2500.ko'  (as root)
        '/sbin/ifconfig ra0 inet YOUR_IP up' 

ive found the readme me and was just wondering where the configured and built kernel would be?
and do i have to specify my ip?

---

