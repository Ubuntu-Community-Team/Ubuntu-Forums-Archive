---
title: "reconfigure grub after reinstall"
date: 2010-10-31
forum: Apple Hardware Users
---

### Post by ichigo on 2010-10-31
I've upgraded the hdd in my macbookpro 5,5 and after installing OSX and refit and copying the ubuntu to its partition with rsync and the live CD, I am now stuck with the problem that refit won't recognize my linux partition.
After reading some forums/wikis etc. I've understood that grub has to be on a partition with linux. However, I'm not able to install grub with
```
grub-install --root-directory=[UUID] /dev/sda
```,
because the MBR of the hdd is not found. According to Refit, there is a mbr and it looks like it's ok... Grub could be installed with blocklists (that's what it says in the error message), however I have no idea what that means and if that is what I want.

Do you have any ideas how I could install grub so that my linux partition is found by refit?

---

### Post by linuxopjemac on 2010-10-31
from an Ubuntu liveCD, you reinstall Grub to your harddisk
```

grub-install /dev/sdX
```
change /dev/sdX it into the device you want

---

### Post by ichigo on 2010-11-01
Thanks for the answer. However, things aren't that easy :(:
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

```
and btw, the code I've posted in my first post leads to
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/[UUID] /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```

[UUID]=UUID of the partition containing linux. The same message appears if the root-directory option points to the efi partition...
 
Any ideas?

---

### Post by srs5694 on 2010-11-01
You might try installing grub-efi-ia32 or grub-efi-ia64, depending on whether your EFI is 32- or 64-bit (probably the latter, but I'm not positive of that). This version of GRUB works within the EFI framework rather than relying on the BIOS emulation used by the grub-pc package. As such, it eliminates the need for a BIOS Boot Partition. This change will also enable you to convert the flaky and downright dangerous [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) into a conventional protective MBR, which is much safer. OTOH, few or no online tutorials describe how to do it this way. I've seen some suggestions that X may work only in non-accelerated framebuffer mode when booting in EFI mode. That's definitely not a problem on my Mac Mini 1,1, but it's possible it's a problem on systems with other graphics chipsets. (Mine's got an Intel chipset, the 950 IIRC.)

---

### Post by ichigo on 2010-11-02
Thankyou very much for your help. On the page you linked to, it says that
> Unfortunately, as of autumn 2010, rEFIt, or some tool associated with it, seems to produce misconfigured hybrid MBRs, requiring elimination of a duplicate 0xEE MBR partition. 
...which might explain my problem. Anyway, I'm going to give grub-efi a shot tonight.

---

