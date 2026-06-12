---
title: "source directory for the linux kernel in 6.06"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by zmr on 2006-12-04
I am attempting to install a new application which asks that I identify the directory where the linux kernel is located. I have been told the linux kernel is often found in the /usr/src/ directory, but do not see it there. Can anyone tell me how I can find the location of the kernel (or where it is placed by default)?

Thanks!

Zach

---

### Post by Bachstelze on 2006-12-04
By default, the kernel source is not installed. If you want to compile something, you'll most likely not need the full surce but only the headers, which you can install with 

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by taurus on 2006-12-04
If you don't have /usr/src, then create it.  Usually the source should be in /usr/src/linux which is actually a symbolic link to /usr/src/linux-2.6.17 or whatever kernel version you are running...

---

### Post by zmr on 2006-12-04
Thanks HymnToLife. I installed the kernel-headers, but still can not install the application. As mentioned, when I run the install script for the application, it asks me to specify the directory of the kernel. I enter the following directory for the kernel-headings, but it the application fails to create a module:

```
/usr/src/linux-headers-2.6.15-27-386
```

Seems like I am doing one or two smalls things wrong and that it should be working with a little more knowledge. Any insights on this??

---

### Post by taurus on 2006-12-04
What app are you planning to install?

---

### Post by zmr on 2006-12-04
Trying to install the Linux version of cisco's VPN Client, which my university makes available for free to students (but offers little support when it comes to installing or configuring applications for Linux).

---

### Post by Bachstelze on 2006-12-04
Then try installing the full source :

```
sudo apt-get install linux-source-2.6.15
```

---

### Post by az on 2006-12-04
> **zmr said:**
> I enter the following directory for the kernel-headings, but it the application fails to create a module:

```
/usr/src/linux-headers-2.6.15-27-386
```??

Is there an error message displayed?  Usually, the source for such modules is smart enough to look in /lib/modules/2.6.15-27-386/build to find the headers or the source.  The linux-headers-xxx packages do make that symlink.

> **zmr said:**
> 
Seems like I am doing one or two smalls things wrong and that it should be working with a little more knowledge. Any insights on this??

It is not your fault.  It is a bug.  You should not have to have intimate knowledge of your OS to build a driver for it -  this is supposed to be reasonably easy.

Is there are README file in the source you were given?  What are the requirements?  Is the module built for an old (2.4) kernel, for example?

---

### Post by az on 2006-12-04
> **HymnToLife said:**
> Then try installing the full source :

```
sudo apt-get install linux-source-2.6.15
```


That won't work.  Installing that package just plops a tarball with the patched kernel source in /usr/src.  Before you can use it to build an extra module, you need to unpack and configure the source to your exact (running) version.

Then, you need to build the kernel so that the headers appear in the right place.

---

