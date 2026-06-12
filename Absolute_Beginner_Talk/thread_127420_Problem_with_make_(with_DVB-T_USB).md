---
title: "Problem with make (with DVB-T USB)"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by Biggz on 2006-02-08
Hi all!

First off let me explain what i'm trying to do.

I'm trying to get my AverMedia DVB-T USB2 (A800) device to work. And i'm following this tutorial. [http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto](http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto)

I got cvs, build-essential, gcc, gcc-3.4 and some other various bits and bobs through Synaptic.

When following that guide I get the source from CVS fine but when i try to "make" i get the following error.

```

biggz@BiggzLaptop:~/dvb-kernel/build-2.6$ make
Makefile:13: /lib/modules/2.6.12-9-k7/source/.config: No such file or directory
make: *** No rule to make target `/lib/modules/2.6.12-9-k7/source/.config'.  Stop.

```

I really dont know if this matters but **lsusb** gave me the following: 
```

Bus 004 Device 002: ID 07ca:a800 AVerMedia Technologies, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

So... any ideas? :) 

Has anyone got any tips to fix what i'm specifically seeing here or any other tips on different routes (if there is any) to get this device working. I'll be so pleased when i can get that thing working as it's the only thing keeping with a dual boot system at the moment.

Thanks for your time.

Biggz

---

### Post by Biggz on 2006-02-09
I've got passed that current problem by recompiling the kernel, at which time i enabled a lot of DVB options.

I dont think this was what was wrong with it initially but it seems to have fixed it as a by product :???: 

So continuing on with this guide [http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto](http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto)

i get to the part involving **modprobe** and **insmod** all of which i get an error with. e.g
```

biggz@BiggzLaptop:~/dvb-kernel/build-2.6$ modprobe i2c-core
FATAL: Module i2c_core not found.
biggz@BiggzLaptop:~/dvb-kernel/build-2.6$ insmod ./dvb-core.ko
insmod: error inserting './dvb-core.ko': -1 Operation not permitted

```

At least i'm going in the right direction, even if it is slowly. With the new information has anyone got any ideas or tips that they could share with me ?

Thanks again.

---

