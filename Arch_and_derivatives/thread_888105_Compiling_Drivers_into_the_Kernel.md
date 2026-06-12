---
title: "Compiling Drivers into the Kernel"
date: 2008-08-12
forum: Arch and derivatives
---

### Post by YodaMstr on 2008-08-12
Alright, so, I figured I'd finally dive into kernel customization and the like pretty soon.  I've read that you can compile drivers into the kernel instead of specifying them as modules.  Could someone tell me, or point me to a guide that explains how to do this?  It'd be appreciated.

---

### Post by Barrucadu on 2008-08-12
Well, for many drivers, you can specify whether to include them within the kernel, include them as modules, or exclude them when you get to the menuconfig/xconfig stage.
If you find a good guide on compiling yourn own kernel it'll explain how, as well as many other useful things.

---

### Post by handy on 2008-08-13
The only time I have done such a thing was when I attempted to install Gentoo, a few times. :lolflag:

Under those circumstances, I was asked all of the questions in a multiple choice scenario.

Let us know if it is the same in Arch please?

---

### Post by Barrucadu on 2008-08-13
Handy, that sounds like the old config program, which isn't really recommended any more as menuconfig is much easier.

---

### Post by handy on 2008-08-13
> **Barrucadu said:**
> Handy, that sounds like the old config program, which isn't really recommended any more as menuconfig is much easier.

How is menuconfig different?

---

### Post by Barrucadu on 2008-08-13
menuconfig is an ncurses interface divided up into categories, rather than a series of questions.
[http://en.wikipedia.org/wiki/Menuconfig](http://en.wikipedia.org/wiki/Menuconfig)

---

### Post by rsambuca on 2008-08-13
I have a related question regarding the kernel and modules.  It would appear that the new .26 kernel will be coming into the core repos shortly.  Can anyone give me a heads up as to what types of things I will have to rebuild after a kernel update?  I am unclear as to what is actually built into the kernel and what is added afterwards.  This will be the first real test as to whether I stick with Arch or not.  If I have to fiddle around re-installing a bunch of stuff too frequently, I will probably lose patience!

---

### Post by handy on 2008-08-13
> **Barrucadu said:**
> menuconfig is an ncurses interface divided up into categories, rather than a series of questions.
[http://en.wikipedia.org/wiki/Menuconfig](http://en.wikipedia.org/wiki/Menuconfig)

The kernel config's that I did were listed in multiple categories on different pages, where I had to choose by ticking or un-ticking a box.

That *sounds* like menuconfig?

***[Edit:]** I just had a look at the menuconfig page you linked to, it really looked much the same as whatever it was called that I did with Gentoo a year or so ago?*

---

### Post by fwojciec on 2008-08-13
> **rsambuca said:**
> I have a related question regarding the kernel and modules.  It would appear that the new .26 kernel will be coming into the core repos shortly.  Can anyone give me a heads up as to what types of things I will have to rebuild after a kernel update?  I am unlcear as to what is actually built into the kernel and what is added afterwards.  This will be the first real test as to whether I stick with Arch or not.  If I have to fiddle around re-installing a bunch of stuff too frequently, I will probably lose patience!

Generally what needs to be rebuilt after kernel upgrade is everything that builds against the kernel, which means 3rd party drivers (wifi, video), things like virtualbox module and such.  Having said that, in Arch usually  kernel and the related modules are moved to the repos at the same time, so in most cases kernel upgrade should be completely seamless and requires no manual rebuilding of anything.  Things can get a bit more complicated if you're using the testing repo, or a custom kernel.

---

### Post by Barrucadu on 2008-08-13
> **handy said:**
> The kernel config's that I did were listed in multiple categories on different pages, where I had to choose by ticking or un-ticking a box.

That *sounds* like menuconfig?

***[Edit:]** I just had a look at the menuconfig page you linked to, it really looked much the same as whatever it was called that I did with Gentoo a year or so ago?*

Ah, I thought you were talking about 'config', which is just a series of questions.

---

### Post by rsambuca on 2008-08-13
> **fwojciec said:**
> Generally what needs to be rebuilt after kernel upgrade is everything that builds against the kernel, which means 3rd party drivers (wifi, video), things like virtualbox module and such.  Having said that, in Arch usually  kernel and the related modules are moved to the repos at the same time, so in most cases kernel upgrade should be completely seamless and requires no manual rebuilding of anything.  Things can get a bit more complicated if you're using the testing repo, or a custom kernel.
Thanks for the info.  The only things I can think of offhand that might be required for me are the nvidia driver, uvc video, and perhaps ivtv stuff.  Maybe instead of blindly agreeing to the upgrade, I will actually take a look as to see what it is doing!

---

### Post by handy on 2008-08-13
> **Barrucadu said:**
> Ah, I thought you were talking about 'config', which is just a series of questions.

The only time's I have ever compiled the kernel was in my multiple unsuccessful attempts to install Gentoo.  So I really don't remember or really understand what you are talking about. :)

It would (possibly) seem that the reason I could not get Gentoo to install at that time was due to a bug in the BIOS of my motherboard.

Anyway, I moved on to greener pastures... :)

---

