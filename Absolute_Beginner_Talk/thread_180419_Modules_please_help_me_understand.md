---
title: "Modules: please help me understand"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by skippy81 on 2006-05-22
Hello all.  

Ok I have searched high and low for this information, but I just don't seem to be able to find it.  

When my system boots various external modules are loaded into the kernel, and when I do an "lsmod" I can see them.  

What I want to know is how these modules are chosen to be loaded at boottime.  I have read /etc/modules file which contains 3 modules to be loaded at boot.  However my lsmod command shows tons of modules.  Doing modprobe -r removes a module for my session, but after I reboot the module is back again. 

Please tell me how these modules are chosen to be loaded.  Is it an autodection program? Or is there a config file which lists them all?  If so where is it?

Thanks

---

### Post by mority on 2006-05-22
Yes, the hardware autodetection decides which modules to load. But how I can't explain how it does that. Some magic I guess.

---

### Post by skippy81 on 2006-05-22
Ideally I would like to be able to choose exactly which modules are loaded.

I won't be changing my hardware at all on this PC for years so I'd kinda like to be able to boil the system down to the minimum modules I need.

---

### Post by mority on 2006-05-23
You will have to build your own kernel in order to achieve that. And if you build your own kernel you won't have to use modules at all anymore because you can choose exactly every single feature and hardware support the kernel should be capable off. E.g. you may compile the support for your NIC directly into the kernel instead of loading a module for the NIC.

But you will have to read a bit and take some time to build your kernel.
Here's a HOWTO: [http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)

Notice that due to the modern fast hardware you won't notice any performance gain by building your own kernel. It is not really recommended any more unless you have a specific reason (like need for support of esoteric hardware). Or you just do it for fun =)

---

