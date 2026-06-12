---
title: "multiple OSes"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by etcher1 on 2006-12-02
Hi all, 
Noobie here, when installing mutiple linux OS in multiple partitions do each of them need to be in the mbr?  I am trying to install fedora core 4 and ubuntu 5.10 on the same hd.
I need all the help I can get!:-?

---

### Post by rsambuca on 2006-12-02
Should be pretty easy to do.  The grub installer that comes with ubuntu should recognize other operating systems - if not, you can add them later.

I currently have 6 different OS's installed, and grub gives me an option of which one to use when I start the computer.

There is also another boot loader program called LILO, which I know nothing about.

Do you have either one installed already?

---

### Post by etcher1 on 2006-12-02
I have fedora core installed 1st, then installed ubuntu 2nd.  It loads ubuntu before it give me a chance to select which one I want to use.  I don't know it it did the fedora in.  I am just now starting to play with linux and have no idea what I am doing. So losing data is not an issue yet.

---

### Post by clarkth on 2006-12-02
> **rsambuca said:**
> I currently have 6 different OS's installed, and grub gives me an option of which one to use when I start the computer.


I'm interested in doing the same thing on a development/test computer.  Can you post your grub file so I can understand how to do this?  Thanks.

---

### Post by Sef on 2006-12-02
> 
Quote:
Originally Posted by rsambuca View Post
I currently have 6 different OS's installed, and grub gives me an option of which one to use when I start the computer.
I'm interested in doing the same thing on a development/test computer. Can you post your grub file so I can understand how to do this? Thanks.

If you are installing Ubuntu last, then GRUB will pick up the other oses.  The default boot will be Ubuntu.  To use another os, you just use the down arrow until the os you want is highlighted.  (Note: last os installed becomes the default.)

---

### Post by rsambuca on 2006-12-02
> **clarkth said:**
> I'm interested in doing the same thing on a development/test computer.  Can you post your grub file so I can understand how to do this?  Thanks.

Just so you know where I am coming from, I have three drives, one with XP, Vista, and a common data partition; one with a a large extended partition consisting of four partitions for the different distros and one common swap, and a large common data partition; and a really old and small 6GB drive formatted as FAT32 to transfer files between Windoze and linux stuff.

This is the menu.lst file from the /boot/grub directory
The grub loader from the last system I installed (Sabayon) actually didn't detect anything other than Windows, so I had to add all the other stuff to get to ubuntu,etc.  There may be better ways, but I am pretty new to this stuff and for now, it does what I need.  Just to note, the windows selection points to the Vista loader, which then selects whether you want XP or Vista.  I don't know how to put them both on separately on this list.  Nothing seemed to work.

I will be eventually cutting down the different OS's but am just testing the waters right now.
```
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd2,8)
#          kernel /boot/kernel-genkernelreal_root=/dev/sda9
#          initrd /boot/initramfs-genkernel
#boot=/dev/hda
default=0
timeout=8
splashimage=(hd2,8)/boot/grub/splash.xpm.gz
title Sabayon Linux x86-64 3.2
        root (hd2,8)
        kernel /boot/kernel-genkernel-x86_64-2.6.18-gentoo-r4  root=/dev/ram0 ramdisk=8192 real_root=/dev/sda9  quiet  init=/linuxrc doslowusb splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 ide=nodma
        initrd /boot/initramfs-genkernel-x86_64-2.6.18-gentoo-r4
title ubuntu 64-bit
        root (hd2,6)
        kernel /boot/vmlinuz-2.6.17-generic root=/dev/sda7 ro quiet splash
        initrd /boot/initrd.img-2.6.17-10-generic
        boot
title Windows
        rootnoverify (hd0,0)
        chainloader +1
title ubuntu 32-bit
        root (hd2,4)
        kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
        initrd /boot/initrd.img-2.6.17-10-generic
        boot
title kubuntu
        root (hd2,7)
        kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda8 ro quiet splash
        initrd /boot/initrd.img-2.6.17-10-generic
        boot

```

---

### Post by clarkth on 2006-12-03
Excellent, thanks!

---

### Post by rsambuca on 2006-12-03
By the way, I had noticed that there is a line that says "savedefault" right above the "boot" line for the ubuntu boot instructions if you look at the menu.lst from an ubuntu install.

when I was adding all of these instructions to the sabayon menu.lst, I forgot to add the "savedefault" line, but things still seem to work.  I haven't had time to check the grub documentation to find out what that actually does.  Anyone know off-hand?

---

