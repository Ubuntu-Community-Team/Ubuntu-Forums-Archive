---
title: "Dual boot question"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Stomstedt on 2006-10-20
My computer is dual booting currently.  When the screen to select which OS i want pops up i get a whole lot of choices when I want only a couple..  Most of them dont even work (i don't know why they're even there) for instance Ubuntu, kernel 2.6.15-27-k7.  How do I remove these and which ones do i need to keep?

Thanks.

---

### Post by Jorge on 2006-10-20
Those entries are old kernel images, look at this thread:

[http://ubuntuforums.org/showthread.php?t=225854&highlight=remove+old+kernel]("http://ubuntuforums.org/showthread.php?t=225854&highlight=remove+old+kernel")

---

### Post by fatsheep on 2006-10-20
It sounds like you need to do a kernel cleanup.  Here's a little guide I wrote, hope it helps you:

[SIZE="4"]**Kernel Cleanup**[/SIZE]
Ubuntu automatically updates the kernel for our convienance.  However, one problem with this is that it leaves the old kernels on our system.  This not only takes up extra space but it clogs up GRUB's boot menu (there will be two options for every kernel you have installed).  In this section we are going to uninstall our old kernels (which will clean up the boot menu).  

First find out what kernel you are using:

> uname -r

On my system, the output of the command is,
> 
2.6.15-27-amd64-generic

This means I am using the 2.6.15-27 version of th AMD 64 Generic kernel.  Your kernel may be different so keep this in mind.  We want to remove all kernels except for the one currently in use (in my case 2.6.15-27-amd64-generic).  Let's open up Synaptic Package Manager and do a search by name for linux-image.  Here are the Linux kernel packages.

[IMG]http://img246.imageshack.us/img246/801/installedkernelsge7.png[/IMG]

The package linux-image-amd64-generic (at the bottom) simply installs the latest AMD 64 Generic kernel.  We want to leave this package alone.  The other three installed packages are the kernels themselves – 2.6.15-23 AMD Generic, 2.6.15-25 AMD Generic, and 2.6.15.27 AMD Generic. 

In my case, I would remove the  2.6.15-23 AMD Generic and 2.6.15-25 AMD Generic kernels.  This leaves me with the kernel currently in use 2.6.15-27 AMD64 Generic and the linux-image-amd64-generic package which is used to install the latest AMD 64 Generic kernels as they become available.

---

### Post by Stomstedt on 2006-10-20
Hey, that helps out a lot, thanks!

---

