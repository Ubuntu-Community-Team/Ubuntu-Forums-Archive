---
title: "[SOLVED] Ubuntu Studio and Virtual Box"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by dysonsphere23 on 2007-06-13
I was running xp in virtual box with no problems in Ubuntu 7.04.  Just upgraded to Ubuntu Studio and my xp will not start.  The following error message comes up:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Is there maybe a compatibility issue?  Should I reinstall virtual box and xp?  It there an easier patch solution?

Thanks in advance

---

### Post by lazyart on 2007-06-13
Your kernel doesn't match anymore.

Do what it says,```
sudo /etc/init.d/vboxdrv setup
```and it should fix itself.  This happens anytime you update your kernel.

---

### Post by starcraft.man on 2007-06-13
> **dysonsphere23 said:**
> I was running xp in virtual box with no problems in Ubuntu 7.04.  Just upgraded to Ubuntu Studio and my xp will not start.  The following error message comes up:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Is there maybe a compatibility issue?  Should I reinstall virtual box and xp?  It there an easier patch solution?

Thanks in advance

By upgrading (or really kinda a horizontal move, its just package changes) I assume your using the low latency kernel. Virtual Box has to be reconfigured every time you change kernels. Its easy enough. Just open up any terminal (Applications > Accessories > Terminal) and paste the line they gave you in:

```
sudo /etc/init.d/vboxdrv setup
```

Let it run and then try VBox again.

Edit: Wuups, too slow :p.

---

### Post by dysonsphere23 on 2007-06-13
I ran that command in a terminal and it created this output:

dysonsphere@Nirvana:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/lib/vbox-install.log to find out what went wrong


The log file says:

Makefile:73: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again..  Stop.

Now I am a bit confused as to where the new kernel is located and where/when to type the directory location.

Thanks

---

### Post by onero on 2007-06-14
Try the suggestions from this thread: [http://ubuntuforums.org/showthread.php?t=458494&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=458494&highlight=virtualbox)

You probably just need to install the headers for the lowlatency kernel, that's what I did when the kernel upgraded last time :)

---

### Post by dysonsphere23 on 2007-06-14
Yes, Thanks.

Installing the headers:

sudo aptitude install linux-headers-$(uname -r) 

and running the setup twice(?):

sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup

did the trick.

Thanks so much for your courteous help.

Peace

---

### Post by starcraft.man on 2007-06-14
No problem. Virtual Box is a great product (using it right now :p) so enjoy it and if you have future questions about it, they have their [own forums]("http://forums.virtualbox.org/") that might get you more specific answers.

Have a nice day. Off to help others.

---

