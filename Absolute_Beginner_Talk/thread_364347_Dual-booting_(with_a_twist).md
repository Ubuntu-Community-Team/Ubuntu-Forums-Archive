---
title: "Dual-booting (with a twist)"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by John E on 2007-02-18
I'm trying to dual-boot between Ubuntu 6.10 and OpenSuse 10.2. OpenSuse was originally installed on my laptop machine as hd0,8. I backed it up and transferred it to my desktop machine, also as hd0,8. hd0,5 is currently used for Ubuntu 6.10 and is the source for Grub. From menu.lst (in OpenSuse) the main boot entry looked like this:-

```
title		OpenSUSE 10.2
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.18.2-34-default root=/dev/hda9 vga=0x314 resume=/dev/hda5 splash=silent showopts
initrd		/boot/initrd-2.6.18.2-34-default
```

So I figured that if I add a similar entry to menu.lst under Ubuntu, Grub would add an option to boot into OpenSuse. After filtering out the irrelveant stuff, Grub's menu.lst now looks like this:-

```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hda6 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title		OpenSUSE 10.2
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.18.2-34-default root=/dev/hda9 vga=0x314 resume=/dev/hda5 splash=silent showopts
initrd		/boot/initrd-2.6.18.2-34-default
savedefault
boot
```

This does indeed give me a new option for OpenSuse and it even starts the OpenSuse boot process. However, about half way through, OpenSuse fails with this error message:-

> fsck failed. The root file system is currently mounted read-only. To remount it as read-write do:

**bash# mount -n -o remount,rw**

OpenSuse then boots into its Recovery console -but if I type the above command I just get a "Usage" message displayed. It seems as though there's no **-n** option for **mount**.

Can anyone shed any light on this and tell me what's needed to dual-boot between them?

---

### Post by solar george on 2007-02-18
You really should reinstall opensuse to get it to run on your desktop.

Otherwise you will have to reconfigure an awful lot - probably at the command prompt.

> kernel		/boot/vmlinuz-2.6.18.2-34-default root=/dev/hda9 vga=0x314 resume=/dev/hda5 splash=silent showopts

Alter the kernel line to mount the root filesytem read write:
```
kernel		/boot/vmlinuz-2.6.18.2-34-default root=/dev/hda9 rw vga=0x314 resume=/dev/hda5 splash=silent showopts
```

This may help, but as I said a clean install would be better.

---

### Post by John E on 2007-02-18
How silly of me...! My laptop's hardware would have been totally different.

Anyway, I did a fresh re-install and it cured the problem. An added bonus was that I got to see OpenSuse's version of Grub. Has anyone seen it? It's incredible - a wonderful. entertaining, animated snow scene (I'm easily impressed).

---

### Post by terdon on 2007-02-18
> 

 fsck failed. The root file system is currently mounted read-only. To remount it as read-write do:

bash# mount -n -o remount,rw




Just a note on the error message, the format for that mount command should be:

```
mount -n -o remount,rw /dev/hda8 
```

But I agree, you should go for a fresh install... I recomend installing ubuntu and then suse, as suse has a very good partitioner and should have no problem installing next to other OSs.

---

