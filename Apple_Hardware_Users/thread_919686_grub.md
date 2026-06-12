---
title: "grub"
date: 2008-09-14
forum: Apple Hardware Users
---

### Post by gatmaster on 2008-09-14
I have a broken MacBook. The hard drive is repeatedly breaking. I have resolved to purchase a external hard drive. Should I use a grub c.d. to load to the external drive ( I can use the internal hard drive to boot to live c.d.s and to boot into single-user-verbose mode ). The other possibility being putting grub on the external hard drive. Which method is better.

---

### Post by pxwpxw on 2008-09-14
> **gatmaster said:**
> I have a broken MacBook. The hard drive is repeatedly breaking. I have resolved to purchase a external hard drive. Should I use a grub c.d. to load to the external drive ( I can use the internal hard drive to boot to live c.d.s and to boot into single-user-verbose mode ). The other possibility being putting grub on the external hard drive. Which method is better.

I asume you are talking about booting ubuntu.

About the only stuff that a macintel MacBook will directly boot from an external drive is an EFI bootloader - i.e. MacOsx , or rEFIt,
or grub-efi. 

MacBook will not boot the grub mbr/bios bootloader from external.

A grub cd wont help, because it probably will not see the external drive - you could try that.

If you can put a reliable boot partition with the kernel on the internal hd, that will be ok.

It really depends on how much you can do with the existing system as it will need experimenting.

rEFIt on a usb stick will boot iself and let you see what is there, but unfortunately cannot boot a grub bios loader, and cant boot linux directly.

grub-efi is a work in progress, no reliable release yet, and tricky to get set up unless you already have a working linux system.

You could check out elilo, I dont know its capabilities for externals
on macintel boxes.

Good luck.

---

### Post by cyberdork33 on 2008-09-15
Is replacing the internal Hard Drive not an option?

---

