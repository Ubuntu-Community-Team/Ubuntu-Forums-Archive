---
title: "Trying to boot from efi"
date: 2011-07-04
forum: Apple Hardware Users
---

### Post by crewkid89 on 2011-07-04
Hi everyone.  I've just purchased my shiny new iMac and am trying to get a dual boot setup going.  For several reasons, I am interested in an efi boot and i followed the directions at

[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

I got all the way to the end successfully but when I try to boot from refit, it drops me into a grub shell.  Any suggestions?

---

### Post by srs5694 on 2011-07-04
You might need to adjust the GRUB prefix. First, you need to locate the GRUB configuration files from within the GRUB shell by using ls:

```

grub> **ls**
(hd0) (hd0,gpt5) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)
grub> **ls (hd0,gpt5)/**
abi-2.6.31-22-generic grub/ initrd.img-2.6.31-22-generic
memtest86+.bin System.map-2.6.31-22-generic vmcoreinfo-2.6.31-22-generic
vmlinuz-2.6.31-22-generic

```

Repeat the second command until you find the partition with the GRUB files (the grub/ directory in this example). You may have an idea of where this is already. In this example, there's a separate /boot partition on /dev/sda5 (aka (hd0,gpt5)), but if you installed without a separate /boot partition, you'll be looking for the Linux root filesystem rather than the /boot filesystem.

Once you've figured out where GRUB is, you can set the prefix, set the root, and launch the menu:

```

grub> **set prefix=(hd0,gpt5)/grub**
grub> **set root=(hd0,gpt5)**
grub> **insmod normal**
grub> **normal**

```

If you don't have a separate /boot partition, you'll need to adjust the path in the first line, to something like (hd0,gpt5)/boot/grub.

Of course, you won't want to do this every time you boot, so you'll need to adjust your configuration files to set the prefix; or maybe you'll need to copy grub.cfg to some other location (onto the EFI System Partition, say). FWIW, I've had better luck with locally-compiled GRUB 2 than with the precompiled binaries that Ubuntu distributes. See [here](https://help.ubuntu.com/community/UEFIBooting) for information on compiling GRUB 2 for EFI systems. I've also had better luck with [ELILO](http://elilo.sourceforge.net/cgi-bin/blosxom) than with GRUB 2 on UEFI systems, although not on my 32-bit 1st-generation Intel Mac Mini. I don't know if ELILO has 32-bit issues or Mac issues or what, though. If you can get the system booted, even via something like [Super GRUB 2 Disk,](http://www.supergrubdisk.org/) it might be worth installing ELILO and trying it out.

---

### Post by crewkid89 on 2011-07-08
I tried your suggestions but I just have not been able to make it work.  I also tried compiling grub2 from source but I got the same result.  I haven't yet tried ELILO. Is there a way to get support for ELILO it seems to be dead?

---

### Post by metatechbe on 2011-07-14
> **crewkid89 said:**
> Hi everyone.  I've just purchased my shiny new iMac and am trying to get a dual boot setup going.  For several reasons, I am interested in an efi boot and i followed the directions at

[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

I got all the way to the end successfully but when I try to boot from refit, it drops me into a grub shell.  Any suggestions?

Hi,

Recent Mac models (from 2010 and higher) are reported not to work "out of the box" with the Linux kernel in EFI mode.
3 possibilities to make it work : 
- Use the kernel v3.0rc7 (or higher), which contains several EFI-related patches.
- Recompile the kernel with the patch "Run EFI in physical mode".
- Use "noefi" kernel parameter, and boot first in BIOS mode with rEFIt, then do a warm reboot in EFI mode.

Please give us feedback on what worked for you.

Thanks.

metatech

---

