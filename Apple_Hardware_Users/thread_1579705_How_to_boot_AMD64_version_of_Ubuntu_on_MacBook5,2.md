---
title: "How to boot AMD64 version of Ubuntu on MacBook5,2?"
date: 2010-09-22
forum: Apple Hardware Users
---

### Post by wpdster on 2010-09-22
I have installed the 64 bit version of Ubuntu on my internal drive on my MacBook5,2.  It boots fine if I add acpi=off to the kernel command line.  But I have a couple of problems with this.  The first is that I don't get ACPI features, so I can't put the computer to sleep just by closing the lid.  The second is that, for somewhat mystifying reasons, I only get access to one core of my dual core CPU.  From what I've read, others have had these same problems on this rev MacBook.

I read a thread somewhere that suggested that if I installed rEFIt and installed grub-efi within rEFIt, then I should be able to regain ACPI and dual core capabilities.  I tried that at some point in the last week and it appeared to work.  However, at that point I was running the 32-bit installation.

The problem is that now (for various reasons) I've had to completely reinstall Ubuntu on this machine.  I decided to install the 64-bit version.  But I can't get it to boot from rEFIt + grub-efi.  (It does boot fine with the default version of grub installed in /dev/sda3, provided that I add acpi=off.)

I'm in a maze of twisty little passages all alike, and would like some help figuring out how to get out.  Can anybody point me at some resources to solve this issue?  I have stumbled across a package (in the official repositories) with the very intriguing name of grub-efi-amd64, but I'm hesitant to just do an "apt-get install grub-efi-amd64" without knowing a little more about it.  I'm a little worried that I'll be left with something that doesn't boot at all.

--wpd

---

