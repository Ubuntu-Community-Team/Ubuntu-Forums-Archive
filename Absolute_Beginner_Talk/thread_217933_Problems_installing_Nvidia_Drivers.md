---
title: "Problems installing Nvidia Drivers"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-17
My [original topic]("http://www.ubuntuforums.org/showthread.php?t=217849") has died so I'm going to start a new one since I'm still struggling with this problem:

I have an AMD64 processor, a Nvidia 6600 GT graphics card, and a X86 version of Ubuntu 6.06.  When I try to install the [AMD64/EM64T Nvidia Drivers]("http://http://www.nvidia.com/object/linux_display_amd64_1.0-8762.html") I got this message:

> ERROR: this .run file is intended for the
Linux-x86_64 platform, but you appear to be
running on Linux-x86.  Aborting installation.


So which drivers should I try to install now?  Here are the two linux choices (excluding AMD64/EM64T): 

[LIST=1]
[*]IA32
[*]IA64
[/LIST]

On a side note, here are the options I get at bootup:

> ubuntu, kernel 2.6.15-26-k7
ubuntu, kernel 2.6.15-26-k7 (recovery mode)
ubuntu, kernel 2.6.15-26-386
ubuntu, kernel 2.6.15-26-386 (recovery mode)
ubuntu, kernel 2.6.15-23-286
ubuntu, kernel 2.6.15-23-286 (recovery mode)
ubuntu, memtest 86+

Other Operating Systems:

Microsoft Windows XP Home Edition


Why are there three different kernels?  Perhaps this has something to do with my problem?

---

### Post by orb9220 on 2006-07-17
your ubuntu installation has multiple kernals which shouldn't even be there.

during boot down arrow to ubuntu, kernel 2.6.15-26-386 and boot that one.
why do you have k7 installed?

and you want to install the nvidia drivers for i32 or 32 bit if you install a kernel that is 64bit then you install the video driver that is I64 bit. Video driver must match bit version of kernel.

ubuntu, kernel 2.6.15-26-386 is 32 bit the k7 and 286 shouldn't even be in the grub menu.

Hope this helps. If I was in yer shoes I would do a clean install but that's Just me.

---

### Post by fatsheep on 2006-07-17
Yea I'm probably going to end up doing  a clean install, thanks.

---

### Post by digby on 2006-07-18
did you ever try to install the driver from the repositories?  I don't remember seeing that in the other thread.

---

### Post by fatsheep on 2006-07-18
> **digby said:**
> did you ever try to install the driver from the repositories?  I don't remember seeing that in the other thread.

Nope I'm not sure how I would do that.  

**Also, I could use some help on uninstalling Ubuntu.** ](*,)

---

### Post by digby on 2006-07-18
> **fatsheep said:**
> Nope I'm not sure how I would do that.  

**Also, I could use some help on uninstalling Ubuntu.** ](*,)

!!!  We have advised you very poorly.  I don't know why someone didn't point this out right from the start:  the nvidia drivers are in the repository.  Run this from the terminal```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
``` Then press ctrl+alt+backspace to restart X.

You're done.

As for uninstalling ubuntu?  Just reinstall over the same partitions, or if you're quitting for good :(, use windows disk management to repartition and format to something that it knows how to use.

---

### Post by fatsheep on 2006-07-18
> **digby said:**
> !!!  We have advised you very poorly.  I don't know why someone didn't point this out right from the start:  the nvidia drivers are in the repository.  Run this from the terminal```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
``` Then press ctrl+alt+backspace to restart X.

You're done.

As for uninstalling ubuntu?  Just reinstall over the same partitions, or if you're quitting for good :(, use windows disk management to repartition and format to something that it knows how to use.

Ah thanks I'll try this after I reinstall.  

I'm not quitting for good btw. :)  I'll make a new topic here if I have trouble installing with the alternate installer.

---

