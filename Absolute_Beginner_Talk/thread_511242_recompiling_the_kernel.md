---
title: "recompiling the kernel"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by groovomata on 2007-07-27
Here's a real newbie question: on a laptop that is working well, what are the benefits to recompiling the kernel?
Is there a performance increase?
Thanks,
Erik.

---

### Post by Majorix on 2007-07-27
If you are really a newbie then don't bother recompiling the kernel. I believe you can mess things up then.

---

### Post by Rui Pais on 2007-07-27
> **groovomata said:**
> Here's a real newbie question: on a laptop that is working well, what are the benefits to recompiling the kernel?
Is there a performance increase?
Thanks,
Erik.

performance?  i doubt it.

hibernate/suspend are very useful functions on a laptop. 
If you have problems with those i would recommend compile using a patch with suspend2... but if they are working, theres no need.

Of course you could do it for fun, or learning...

---

### Post by groovomata on 2007-07-28
Would not recompiling the kernel speed things up a little since unneeded code would be cut out to make it leaner?

---

### Post by nick_h on 2007-07-28
Yes - you may well get increased performance and reduced boot times.  Have a look at the [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158) for more information.  There is also a wiki page [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

---

### Post by Rui Pais on 2007-07-28
> **groovomata said:**
> Would not recompiling the kernel speed things up a little since unneeded code would be cut out to make it leaner?

I doubt that with a recent computer one can feel any difference. 
Unless you compile using some patch tweaked for speed, and know your way around kernel options in order to remove a lot of stuff, not necessary that default Ubuntu kernel brings enabled.

Just recompile the Ubuntu kernel and set for your cpu, don't do any special difference. 
And disabling modules don't for sure do any difference at all, since modules are only heavy if they are loaded. 

It's fun to do it (I use viper sources and a very striped, light config) but keep in mind that you can easily end with a non-bootable kernel, or if you choose some very wild patch set to an unstable system or even one that can cause data corruption. 
Just the typical warnings.

:)

---

### Post by groovomata on 2007-07-29
Thanks for your responses folks! I'll take a look at the master kernel thread and the wiki, thanks for the links!
Erik.

---

