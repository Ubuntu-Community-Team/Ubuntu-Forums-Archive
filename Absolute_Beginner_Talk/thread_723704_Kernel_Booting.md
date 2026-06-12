---
title: "Kernel Booting?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by ffejrey on 2008-03-13
I've been looking around as to how to troubleshoot a boot problem on the Live CD.  I am just curious as to what it the boot parameters actually mean.  Specifically quiet and splash.  What am I changing by removing this?  Is there a good guide that shows me what all of the options are and what they do?

Thanks in advance.

---

### Post by spiderbatdad on 2008-03-13
Here ya go: [https://help.ubuntu.com/7.04/installation-guide/i386/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-parms.html)
And see the link to Linux Boot Prompt How To at the top of the page, linked above.

---

### Post by ffejrey on 2008-03-13
Thanks.

At a quick glance it doesn't mention quiet or splash, is that something different then the kernel boot options?

---

### Post by spiderbatdad on 2008-03-13
It is a boot option. That wiki is intended for trouble shooting, something most users should not have to do. Ubuntu does a great job of detecting most hardware, but one has to realize, in most cases, currently, Ubuntu is not factory installed...though this is changing. "quiet splash" hides the verbose CLI output of the boot process, I believe. Common options like noapic acpi=no nolapic control pci assignments and irq polling.
From the install options screen you can press f6 to add parameters to the kernel line. By pressing f1 you will get some brief explanation and f3 or f6 again will show some examples with further explanations.

---

### Post by PeterJS on 2008-03-13
Specifically to the splash and queit options. Splash displays the splash screen with the loading bar, while quite supresses the text messages telling you all the details of the boot process. If you use splash without quiet, you'll get the usual loading bar with a smaller screen inset below it with the boot text. I've never tried quiet without splash, I imagine it'd be quite boring staring at a black screen until gmd started up.

---

