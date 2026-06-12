---
title: "Help installing thinkpad-acpi"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Tribis on 2008-02-12
I'm trying to install the latest thinkpad-acpi, it comes in a tar.gz folder. When I extract it, it extracts to a .patch file. How do I install the .patch? I've been searching for awhile and can not find anything that I can understand.

I need to get this installed to hopefully fix the Standby option on my Thinkpad T41p.

---

### Post by dstew on 2008-02-12
I believe you have downloaded a kernel patch file. This file is meant to "patch" (replace) source code in the kernel with its own. The only way to get this patch into a working kernel is to compile the kernel yourself, after patching the kernel source code.

You can do this, but it might take some learning. The [patch]("http://linux.die.net/man/1/patch") command is what actually puts the patch into the kernel source code. You can install the patch command using synaptic. See [this page]("https://help.ubuntu.com/community/Kernel/Compile") for information about using kernel source code and compiling. [Here ]("http://ccgi.philfam.co.uk/wordpress/")is a page by someone who applied this patch to their kernel.

---

### Post by Tribis on 2008-02-12
Wouldn't this be erased then if and when I upgraded to a newer kernel?

Is there a simpler way to fix the suspend/hibernate problem by simply editing a config file?

---

### Post by dstew on 2008-02-12
Yes, it would be erased. You would be making your own private kernel. What problem are you having with standby?

---

