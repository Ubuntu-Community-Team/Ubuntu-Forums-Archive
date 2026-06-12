---
title: "Can ATI mac suspend problem be solved by custom kernel?"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by E Gardner on 2007-10-23
So, I am aware that the 7.10 Ubuntu kernel is incapable of successful suspend/resume in Macs that use ATI drivers. Has anyone found a way to get around this problem by compiling a custom kernel? Would this even be possible?

I would like to try this myself if I can figure out how to do it - I have a first generation MacBook Pro, and the ATI-related suspend problems have been a thorn in my side ever since I first started experimenting with Linux. This is the last potential solution to this problem I can think of.

If people posted their own experiences or advice about doing this, that would be helpful. I was planning to use a recent vanilla kernel and apply the mactel patches (as described in another thread here) - is that all I need?

One thing that I am most confused about is how to recompile a new fglrx driver after making a new kernel - what do I do with the old driver after this is done? Should I uninstall it before making a new kernel? If I did this, I would have to do everything from the command-line, which could be difficult.

Also, how would I keep the automatic updates from ruining a custom kernel/driver combination after it has been put together (assuming I get that far)?

---

### Post by cyberdork33 on 2007-10-23
> **E Gardner said:**
> So, I am aware that the 7.10 Ubuntu kernel is incapable of successful suspend/resume in Macs that use ATI drivers. Has anyone found a way to get around this problem by compiling a custom kernel? Would this even be possible?maybe, but doubt it. Since the problem is the fglrx module, an open source alternative to that would be best. However, that is not near ready yet.

> I would like to try this myself if I can figure out how to do it - I have a first generation MacBook Pro, and the ATI-related suspend problems have been a thorn in my side ever since I first started experimenting with Linux. This is the last potential solution to this problem I can think of.

If people posted their own experiences or advice about doing this, that would be helpful. I was planning to use a recent vanilla kernel and apply the mactel patches (as described in another thread here) - is that all I need?See posted info in FAQ.

> One thing that I am most confused about is how to recompile a new fglrx driver after making a new kernel - what do I do with the old driver after this is done? Should I uninstall it before making a new kernel? If I did this, I would have to do everything from the command-line, which could be difficult.Be sure you use the correct driver version number that you have when you use the comamnds.
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.40.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.40.4_Driver_Manually)

> Also, how would I keep the automatic updates from ruining a custom kernel/driver combination after it has been put together (assuming I get that far)? I don't know that it would... maybe on a complete kernel update, but wouldn't you want to try it first?

---

### Post by cyberdork33 on 2007-10-23
Update. This will not be fixed until ATI updates their drivers

> **"Gutsy Gibbon Release Notes"]
**Suspend to RAM with fglrx**
[LIST]
[*] Attempting to suspend to RAM using the proprietary fglrx ATI video driver from the restricted component will hard-lock the system due to changes in the kernel's memory allocator (which will be the default in Linux 2.6.23) that have not been followed by ATI in a timely fashion said:**
> Bug #121653[/URL][/LIST]

---

### Post by E Gardner on 2007-10-23
So the kernel change that keeps this from working is not a ubuntu-specific thing, but a problem that will become standardized in all newer versions of the Linux Kernel itself, regardless of distribution? That is really unfortunate.

---

### Post by E Gardner on 2007-10-23
In the bug description for this, there is a lot of discussion of SLAB/SLUB (I am assuming these are kernel components) and switching from one to the other being the source of the problem. Can anyone describe what these things actually are?

---

### Post by greg.hagen on 2007-10-23
I have fglrx and suspend working in gutsy. I just loaded Feisty's kernel (8.6.20-15) and installed fglrx from ati's website.

I'll make a guide if I get the time.

---

### Post by cyberdork33 on 2007-10-23
> **E Gardner said:**
> In the bug description for this, there is a lot of discussion of SLAB/SLUB (I am assuming these are kernel components) and switching from one to the other being the source of the problem. Can anyone describe what these things actually are?

It can be easily switch in the kernel options if you make your own kernel.

I believe it has to do with memory allocation. Do not blame changes in linux, they have been announced coming for a very long time... ATI has not made the needed changes to their driver.

---

