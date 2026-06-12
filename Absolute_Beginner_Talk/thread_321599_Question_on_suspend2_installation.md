---
title: "Question on suspend2 installation"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-19
Hi,

I'm trying to install suspend2 to enable hibernation on my laptop running 6.10. I've successfully patched and compiled the new kernel (2.6.19 vanilla) with Suspend2 and other patched but there is something I don't understand on the Suspend2 HowTo. The instructions are below. What is this initrd/initramfs all about?? Do I need to do the recommended changes? Can somebody explain me how to apply these changes, I really don't understand from the instruction below. Oh and do I need to apply these change before rebuilding the kernel (kernel is now buiding...)?

Thanks a lot! 

-------------------------------------------
Initrd/Initramfs's with Suspend2

Using an initrd/initramfs with Suspend2 is possible, but you will have to trigger a resume yourself in your linuxrc/init. To do this, you MUST either modify your distro's initrd/ramfs generation routines or edit your linuxrc (or init) script yourself to contain the line

    echo > /sys/power/suspend2/do_resume 

Either way, this call must come BEFORE your initrd/ramfs mounts your filesystem. If the line is missing, your system will not resume. If the line comes after mounting file systems, you will most likely suffer from filesystem corruption. You have been warned.

This will work with most initrd setups produced by the various mkinitrd's. If you however use a kernel command-line containing something like

    root=/dev/ram0 init=/linuxrc 

as is described in linux/Documentation/initrd.txt, it will not work. You're probably better off porting your setup to use an initramfs instead.

You can now recompile your kernel with Suspend2...
-------------------------------------------------------

---

### Post by tuxers on 2007-03-09
I have the same problem!

Does Ubuntu have initrd generation scripts, in case where?

---

### Post by nightfrost on 2007-03-20
I'm interested in this as well. I'm running a custom kernel and my computer seems to hibernate just fine, but then it won't resume...

---

### Post by Nigel_C on 2007-04-10
> **kilou said:**
> I'm trying to install suspend2 to enable hibernation on my laptop running 6.10. I've successfully patched and compiled the new kernel (2.6.19 vanilla) with Suspend2 and other patched but there is something I don't understand on the Suspend2 HowTo. The instructions are below. What is this initrd/initramfs all about?? Do I need to do the recommended changes? Can somebody explain me how to apply these changes, I really don't understand from the instruction below. Oh and do I need to apply these change before rebuilding the kernel (kernel is now buiding...)?


For Ubuntu, you will need to do the modifications for your initramfs. This bug report:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/75616](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/75616)
should help.

Regards,

Nigel

---

