---
title: "[SOLVED] new kernel upgrade wont install"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by baracuda68 on 2007-12-20
Hi.   Using Gutsy, 
The current kernel upgrade wont install. I get the message , with adept:
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 

With apt-get I get this:

bob@baracuda:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/18.5MB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 174800 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.46 (using .../linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.22-14-generic/kernel/drivers/net/ppp_generic.ko')
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have the updates "available icon" sitting in my tray bugging me now and it wont go away because of this.

Any ideas??:confused:

---

### Post by baracuda68 on 2007-12-20
**bump**:guitar:

---

### Post by PmDematagoda on 2007-12-20
Remove that package using:-

```
sudo rm /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb
```

Then try updating the kernel again.

---

### Post by baracuda68 on 2007-12-21
> **PmDematagoda said:**
> Remove that package using:-

```
sudo rm /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb
```Then try updating the kernel again.


This worked great! Thanks.

---

