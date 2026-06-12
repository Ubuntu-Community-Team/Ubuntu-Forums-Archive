---
title: "rt2500 Native Linux Driver"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by .oops on 2007-03-19
I'm not quite following this explanation:

```
=======================================================================
Build Instructions:
====================
For 2.4 series kernel:
a. $tar -xvzf RT2500-Linux-STA-x.x.x.x.tar.gz
    go to "./RT2500-Linux-STA-x.x.x.x/Module" directory.

b. Use 'chmod 755' command to change access right of following script files :
   'load', 'unload', 'Configure'

c. run 'cp ./2.4.x/Makefile .' and 'cp ./2.4.x/load .'

d. $make config         # config build linux os version

e. $make all            # compile driver source code

f. $load                # load/insmod module(rt2500.o)

Note: Script functionality:
load            load module to kernel
unload          unload module from kernel
Configure       retrieve linux version


For 2.6 series kernel:
a.  run 'cd STA/Module'
        'cp ./2.6.x/Makefile .'
        'cp ./2.6.x/load .'

b.  $make -C /path/to/source SUBDIRS=$PWD modules
    Where /path/to/source is the path to the source directory for the (configured and built) target kernel.

c.  run '/sbin/insmod rt2500.ko'  (as root)
        '/sbin/ifconfig ra0 inet YOUR_IP up'

```

Especially in step **b** of the **For 2.6 series kernel:** part. Thanks :)

---

### Post by Bachstelze on 2007-03-19
Path to source is /lib/modules/$(uname -r)/build

---

### Post by .oops on 2007-03-19
So I copy **'Makefile'** and **'load'** to it right? Using **$make -C /path/to/source SUBDIRS=$PWD modules**, right?

---

### Post by Bachstelze on 2007-03-19
```

cd STA/Module
cp ./2.6.x/Makefile .
cp ./2.6.x/load .
make -C /lib/modules/$(uname -r)/build SUBDIRS=$PWD modules
```

---

