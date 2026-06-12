---
title: "Ubuntu Bootloader - Mac Mini"
date: 2013-09-27
forum: Apple Hardware Users
---

### Post by art4 on 2013-09-27
Hi Guys,
Beginner here. I tried to install Ubuntu 10.13 on my Mac mini, but it didn't work twice
(after it was installed it wouldn't boot) ....something about not finding the root disk.

But the bootloader did work, it was only when I selected Ubuntu it wouldn't boot,
but I was able to select Windows 7, and Mac OS.
Is there a way to use that bootloader on another drive?

Normally when you start a Mac, you have to hold Alt to select a boot drive.
I would like this menu to come up every boot, like it currently does if I set the Ubuntu HDD as the startup disk.
(but it is a USB drive, and may not be connected, and I want to delete it.
Cheers, Art.

---

### Post by ian-weisser on 2013-09-27
No such release as 10.13. Doesn't exist.
If you meant 13.10, that is currently a pre-release versions intended for testing by users who understand how to troubleshoot and to file bug reports. An inappropriate choice for your skills.

---

### Post by art4 on 2013-09-27
That was just the latest version.
What would you suggest?

... and the bootloader I asked about DID work.
I was trying Ubuntu out of curiosity, but am more interested in the bootloader.
Even if I try another one, and it doesn't work, I would still like to use the
bootloader if it is possible.

> **ian-weisser said:**
> No such release as 10.13. Doesn't exist.
If you meant 13.10, that is currently a pre-release versions intended for testing by users who understand how to troubleshoot and to file bug reports. An inappropriate choice for your skills.

---

### Post by david98 on 2013-09-27
I suggest you download and install ubuntu 12.04 It is a LTS (long term support) so is stable stick to that till 14.04 comes out. It should solve any of the problem's you are having. Remember to back up any data you may have

---

### Post by art4 on 2013-09-27
> **david98 said:**
> I suggest you download and install ubuntu 12.04 It is a LTS (long term support) so is stable stick to that till 14.04 comes out. It should solve any of the problem's you are having. Remember to back up any data you may have

Thanks, I will give it a go, but maybe I'm asking the question wrong.

---

### Post by morgan4 on 2013-09-27
The bootloader for Ubuntu is either GRUB legacy or GRUB2. I don't know if that can be installed separately, but I know it is included in Ubuntu installs. Maybe a Google search?

---

### Post by art4 on 2013-09-27
I'll give it a search, the next iso is still downloading.
Even if this one works, the loader is still on the wrong drive.
You've already got to hold Alt to select a boot drive, then this menu is shown,
so you have to make the same choice again.
You would have already made the choice of op systems when you selected the Ubuntu boot drive.

The major issue for me is that my Alt key doesn't always work because my wireless USB
keyboard doesn't always kick in before my Mac's BIOS checks the keyboard at boot time.
Having this menu on the internal drive would be awesome.

---

### Post by oldfred on 2013-09-27
Moving thread to Apple sub-forum where those who may know about your mini will be. 

I do not know Macs but some links on info.
 32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

 Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

### Post by art4 on 2013-09-27
> **oldfred said:**
> 
I do not know Macs but some links on info.
 32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[l]("http://www.rodsbooks.com/ubuntu-efi/index.html")

Thanks, It is a newer Mac I5 & 2Gb RAM.. not the machine because it ran a 10.10 from a HDD salvaged from
a junked PC, but needed a wired connection, and couldn't update itself anyway. The USB booted demo also goes fine.

12.04 I tried installing twice. It actually tried to do what I want by default, and put the boot loader
on the main drive both times, and failed both times. Both times it offered to install the boot loader on
another disk, but didn't look like it actually tried when I asked it to, because it didn't come out of it as a bootable drive.

---

### Post by oldfred on 2013-09-27
With Mac it will be gpt partitioned. Not sure if you install in UEFI mode or BIOS mode as Mac have an older UEFI that is not fully compatible with new Ubuntu UEFI, but some have seemed to make it work with UEFI. Others have it in BIOS mode.
I think you may want to look at rEFInd.
       Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

