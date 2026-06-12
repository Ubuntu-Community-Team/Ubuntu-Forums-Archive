---
title: "first kernel config"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by gl1756 on 2006-04-11
I've just encountered a situation where I have to configure the kernel. The commands listed are:
cd /usr/src/linux
make menuconfig

however the src folder of my Ubuntu installation (breezy-badger) is empty, so I guess I'm missing the required sources

what would be the easiest way to get them installed? Are they available thru Synaptic? If yes what do I need to select?

thanks much,
gl1756

---

### Post by cleverselfreferentialname on 2006-04-11
Look at this guide: [http://www.ubuntuforums.org/showthread.php?t=85064&highlight=recompilation](http://www.ubuntuforums.org/showthread.php?t=85064&highlight=recompilation) if thats the one you're using, you've forgotten to install the package linux-tree.

---

### Post by az on 2006-04-11
Why do you need to recompile the kernel?  If you need to add a driver (module) just use the linux-headers package instead of the full linux source.

Find the corresponding linux-headers package for your running kernel and install it.  It will create a symlink in /lib/modules/(kernel version)/build that will point to the headers.  A properly built module source will look there and use that automagically.

What do you need to do exactly?  Having to recompile the kernel is very uncommon.

---

### Post by gl1756 on 2006-04-12
[QUOTE=cleverselfreferentialname]Look at this guide: [http://www.ubuntuforums.org/showthread.php?t=85064&highlight=recompilation](http://www.ubuntuforums.org/showthread.php?t=85064&highlight=recompilation) if thats the one you're using, you've forgotten to install the package linux-tree.[/QUOTE]

thanks that did it
I ended up doing it with Synaptics instead but it was good to get a list of required packages and some additional hints

---

### Post by gl1756 on 2006-04-12
[QUOTE=azz]What do you need to do exactly?  Having to recompile the kernel is very uncommon.[/QUOTE]

well, just getting my hands dirty...
I think it's good to know how these things work
(I'm a developer but new to Linux)

thanks for the info

---

