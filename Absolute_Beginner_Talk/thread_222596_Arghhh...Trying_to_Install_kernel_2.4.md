---
title: "Arghhh...Trying to Install kernel 2.4"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by abijah on 2006-07-25
I have the most recent download of Ubuntu and I'm trying to install kernel 2.4 on it.

I keep getting error when I attempt to build it kernel.

I'm following the help files on this forum, but they don't work. :???:

---

### Post by fabiand on 2006-07-25
Hey,

Ubuntu debpends on many features only provided by current (bleeding edge) 2.6 linux kernels.
I suppose that you won't be able to run a stock Ubuntu with a 2.4 kernel.
You will have to remove a lot of services ...

---

### Post by Sef on 2006-07-25
> Trying to Install kernel 2.4

Why do you want to install it instead of having 2.6?

---

### Post by abijah on 2006-07-25
I need kernel 2.4 to develop and test driver.

Please forward info to me.

It looks as tho i might have to ditch this distro and look 4 another, b/c i'm not getting this to work.

---

### Post by az on 2006-07-25
Ubuntu has been using 2.6 kernels for almost two years.  Are there any distros still using a 2.4 kernel?  Debian Sarge does, I think....

---

### Post by matthew on 2006-07-25
[It's in the repos here.]("http://packages.ubuntu.com/dapper/base/kernel-image-2.4.27-2-386")

sudo apt-get install kernel-image-2.4.27-2-386

That should take care of it...

---

### Post by abijah on 2006-07-25
Thanks very much!

However, this is my output when i try that command

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-image-2.4.27-2-386

---

### Post by abijah on 2006-07-25
Ok Matthew... I follow what your saying.

"apt-get install" can't find "kernel-source-2.4.27" and "kernel-tree-2.4.27" in devel [[http://packages.ubuntu.com/dapper/devel/]](http://packages.ubuntu.com/dapper/devel/]) either

i download kernel-image-2.4.27-i386_2.4.27-12.tar.gz manually and  the "bin/" was empty?

I'm kinda confused? Can i mix what i have with source from somewhere else?

---

### Post by matthew on 2006-07-25
The kernel package I mentioned is in the universe repository. Follow this link to [enable the extra repositories]("http://www.psychocats.net/linux/sources.php"). Then try the command I mentioned again. This will install a working 2.4 kernel and set it up in grub for you so you can boot from it without having to compile one yourself. 

NOTE: the link above was for Ubuntu 5.04 and 5.10. For 6.06 the idea is the same as 5.10, except everywhere where the repositories say "breezy" you need to have the word "dapper."

You can also use Synaptic to install it as well as browse for kernel headers, etc. if you need them.

---

