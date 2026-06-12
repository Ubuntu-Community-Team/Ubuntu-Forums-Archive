---
title: "Problems with Mactel-patches and kernel baking. (Edgy Eft / Macbook Pro)"
date: 2007-02-25
forum: Apple Intel Users
---

### Post by cocoia on 2007-02-25
Hello fellow Ubuntu users,
I am currently in the process of getting back into Linux for a more free and feature-rich platform. So far, it's been very good in Edgy, with the GRUB install procedure working flawlessly (sometimes, very rarely, I get a Kernel Panic on boot, but it will just disappear on reboot).

However, since my Macbook gets very hot and I want some more control over it's doings, I am in the process of trying to build a custom kernel, preferably a recent one with the mactel-patches. I asked some questions here and there on the  forum and I finally got a kernel (2.19.5 and 2.18.5)  on which the mactel-patches apply cleanly.

I followed some instructions on the Gentoo Macbook howto, and I set the kernel up with menuconfig, did a make -dpkg, then attempted building the kernel. Halfway there, it quits with an error;

```
> drivers/acpi/blacklist.c: In function `blacklist_by_year':
> 
> drivers/acpi/blacklist.c:82: error: `efi_enabled' undeclared (first
> use in
> this function)
> 
> drivers/acpi/blacklist.c:82: error: (Each undeclared identifier is
> reported
> only once
> 
> drivers/acpi/blacklist.c:82: error: for each function it appears in.)
> 
> make[2]: *** [drivers/acpi/blacklist.o] Error 1
> 
> make[1]: *** [drivers/acpi] Error 2
> 
> make: *** [drivers] Error 2


```

This has been up on the mactel-mailing list, but so far no answer, and I wanted to know if I am on the right path here. People who have a custom kernel working on their Macbook Pro, - please contact me, as I have no idea how you did it ;).

What kernel can you recommend? Should I go with the recent 2.6.20? Can I make my applesmc module work any other way? Touchpad and everything are very secondary to me, but setting a minimal fan speed would be very nice.

Help is very appreciated!

EDIT: I wanted to send Jason Parekh an email about this, as he is the author of the newer minimal -fan-  speed  patch , but his site is down. Meh .

---

### Post by jasonparekh on 2007-02-25
Hey Sebastiaan,

Thanks for letting me know my site is down

I'm not sure about those specific errors you're getting, but I can show you how to build 2.6.20.1 with mactel patches the Debian/Ubuntu way.  I just did this the other day (less than a couple weeks ago) without any errors, so hopefully you won't get any either.

0) Install packages kernel-package and dialog along with: (stolen from /usr/share/doc/kernel-package/README.gz)

The packages suggested are:
devel:        gcc, libc5-dev/libc6-dev, binutils, make, and, for intel
              x86 platforms, bin86 (non-Intel platforms don't need
              this), modutils (or module-init-tools for 2.5.x+ kernels).
interpreters: awk, which is contained in either the mawk or gawk packages
base:         gzip, shellutils, and grep.

1) Download the 2.6.20.1 vanilla source from kernel.org:  [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.1.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.1.tar.bz2).  Extract in /usr/src.

2) Get the SVN of mactel-linux patches:  svn co [https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux](https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux) mactel-linux .  Let's say you're doing this in /usr/local/src.

3) Go into the /usr/local/src/mactel-linux/trunk/kernel/mactel-patches-2.6.20 .  Type ./apply /usr/src/linux-2.6.20.1 . Hopefully they all applied cleanly (I just realized I was using 2.6.20 source and not 2.6.20.1).

4) Go into /usr/src/linux-2.6.20.1 , type make menuconfig .  You can tweak whatever options you want, otherwise leave it default (hopefully once you have it building successfully, you can figure out which options work best on your MBP).  Exit and save the config.

5) Type: fakeroot make-kpkg --initrd --revision=custom1 kernel_image

6) After compile, you should hopefully have a package in one directory up (/usr/src).

I think these are probably the same steps you were following, but hopefully with the latest kernel and mactel it will apply/compile cleanly.

jason

---

### Post by cocoia on 2007-02-27
OK, it all does apply cleanly now, except for your patch. That really sucks because it's the only feature I want to use.

I did, owever, manage to get a .19 kernel working without acpi_blacklist. I am using bootcamp, so it shouldn't be an issue according to the mactel wiki. However, it does not boot- a 7 procent, when the appletouch / ussbhid modules are loaded. I selected them as builtin. I followed the modprobe.d usbhid/appletouchs howto, which suggests you have to put a file in your /modprobe.d folder with some commands, but it doesn't boot still - just hangs at 7.17.

Any suggestions?

---

### Post by das_syndrom on 2007-02-27
Hi!

With the "new" (actually 3 weeks old) mactel patches for 2.6.20 kernels, it is possible (_without_ extra application of jasons patch) to modify the minimum fan speed.

sudo sh -c "echo 2500 > /sys/devices/platform/applesmc/fan0_minimum_speed" should do the job.

Andi

---

### Post by cocoia on 2007-02-28
That's brilliant, das_syndrom, I will be building the kernel immediatly!

Thanks a lot :)

---

### Post by mustang on 2007-02-28
Has there been any progress on the suspend to ram front? Would you any feisty testers or bleeding edge kernel testers mind chiming in on that?

---

### Post by cocoia on 2007-02-28
OK, enormous issues arose from a simple build and dpkg -i.

Apparently, this has made GRUB unable to do anything. When I now boot from rEFIt, the screen remains black, the front LED on the MBP goes off, and the fans kick on as the laptop gets a lot hotter. It just stops there, no image, nothing. There seems to be no way to get feedback from the system. God, this sucks.

Any ideas?

---

### Post by das_syndrom on 2007-02-28
Hmm. :confused: 

What have you exactly done?
Try booting from the live-cd and edit /boot/grub/menu.lst manually. Maybe the installation of the new kernel-package has broken something in it (although i really can't believe that...)
Andi

---

### Post by Gen2ly on 2007-03-01
The grub will not be written to correctly (or, at least has been my experience) when installing a new kernel.  Written to correctly that is for the MBR - EFI hybrid MacIntel boot system.  You will have to restore grub.

This is the page I use:

[How to restore grub from the live cd]("http://www.ubuntuforums.org/showthread.php?t=224351")

I had to use the second part where /proc and /dev need to be mounted, but try the first part first. :)

---

