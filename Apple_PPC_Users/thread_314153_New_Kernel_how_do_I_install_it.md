---
title: "New Kernel how do I install it??"
date: 2006-12-07
forum: Apple PPC Users
---

### Post by applemacmad on 2006-12-07
Ok, I'm a bit of newbie at Linux.
Is it possible to install this new linux kerenel in PPC in Edgy?
If so, could someone tell me how?

Thanks

---

### Post by bernied on 2006-12-07
Where did the kernel come from? Did you get it through your package manager? If so, it is probably already installed. But it won't be running until you restart the machine (because the kernel is the operating system). If you want to know whether it is running or installed, try some of these things:
```
uname -r
```
- tells you the kernel version currently running
```
cat /boot/grub/menu.lst | grep kernel
```
- this will give you all the lines in your boot configuration file with the word 'kernel' in them, ignore the lines beginning with '#'

Post the output of those commands here if you can't figure it out, and tell us where this kernel came from.

---

### Post by stream303 on 2006-12-07
See these relevant threads about installing your own kernel:

[http://www.ubuntuforums.org/showthread.php?t=299360&highlight=fan+control](http://www.ubuntuforums.org/showthread.php?t=299360&highlight=fan+control)

I used these directions to compile a custom 2.6.19 for Edgy.  Note that with this kernel, you no longer have to worry about editing your Makefile for stack-protection.

In it, you'll find what packages you'll need to compile, how to get the kernel, and how to modify yaboot.conf

---

### Post by applemacmad on 2006-12-07
Thanks, that guide was the sort of thing I was looking for

---

### Post by stream303 on 2006-12-07
No problem.  Personally, in make menu_config, I chose using a kernel frequency of 1000hz, and let CPQ become the default scheduler as well.

---

