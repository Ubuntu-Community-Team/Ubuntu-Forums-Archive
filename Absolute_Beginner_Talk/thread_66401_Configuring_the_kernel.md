---
title: "Configuring the kernel"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by ricesteam on 2005-09-17
Hi i'm a complete noob,

I am trying to get my IBM laptop working 100% with linux but it requires me to configure the kernel and and recompile it....but i don't know how.  I searched for a tutorial, but im getting too many hits and I don't know which tutorial is the right one im looking for.

More specifically, [http://www.thinkwiki.org/wiki/How_to_make_ACPI_work](http://www.thinkwiki.org/wiki/How_to_make_ACPI_work) is telling me what to do, but not how.

Does recompiling the kernel mean the same thing as getting a new kernel and compiling it?  I don't have any problems with my current kernel except I just need to configure it to enable some features.  I don't need a new kernel.

Also where is the .config file? Where do i run commands like make config, make xconfig or make menuconfig?? That is what the guides I've been looking at lacked; sure they have locations, but for different distros.

And compiling a new kernel looks like a daunting task esp. to a noob;  So many steps.  I'm sure what I want to do is a lot simpler.

Any help will be greatly appreciated.

Thanks.

---

### Post by aysiu on 2005-09-17
You're a complete noob? I'm an incomplete noob--I've used Linux for only five months, and I've never had to recompile a kernel. Can you explain a bit why you think you have to recompile it?

---

### Post by ricesteam on 2005-09-17
Click on the link i have provided and follow its instructions.

---

### Post by aysiu on 2005-09-17
[QUOTE=ricesteam]Click on the link i have provided and follow its instructions.[/QUOTE] Why? I don't even know what ACPI is. And I'm not trying to recompile my kernel. My question for you is "Why do you think it's necessary to recompile your kernel?"

---

### Post by az on 2005-09-17
Those kernel options are already there.

A kernel option can be compiled into the kernel, be compiled as a module that can be loaded, or not be compiled.

If all the options were turned on, your kernel would run really slow, if it ran at all.  Using modules and loading them when you need them is the way it is done.  It used to be that when you installed linux (years ago) you would use the stok kernel which had reasonable kernel options to get you started, and then compile and install a kernel which suited your needs.  Nowadays, most of the kernel modules are prebuilt and you can load them if you need.

Compiling a kernel is not too hard, but I do not think you need to do it.

By all means, go to the UserDocumentation page on the wiki and roll your own kernel.  It is fun.

So, what problems are you having to make you think you need a different kernel?

---

### Post by ricesteam on 2005-09-18
I'm trying to get my IBM Thinkpad functions to work. Ie Suspend, Hibernate, trackpoint etc...

So far they dont work and I'm under the assumption that my kernel has not set up correctly.

From ThinkWiki.org, it says to get those functions working, I have to enable acpi to get it working.

I've checked the laptop forums, and all sources point to ThinkWiki.  Very good site for info on installing distros on IBM laptops, but its not newbie friendly.

---

### Post by Zoglarfy on 2005-09-20
I have a Thinkpad as well, and am trying to get those functions working.  If you go to the [Ubuntu packages site](http://packages.ubuntu.com/) and search under descriptions for "Thinkpad," you get several packages that you can install.  

I've installed all of them, but it still doesn't seem to work.  It doesn't recognize the "Thinkpad" module.  If I could figure out how to activate it as a module, I think we'd be set.  I'll let you know if I figure it out.   :)

---

### Post by az on 2005-09-20
Did you try Breezy?  I think laptop support is a top priority, so it should be better and better...


If it still does not work, try looking for a bug report about it.  Add to it, if you can.  It may get fixed before breezy releases.

---

