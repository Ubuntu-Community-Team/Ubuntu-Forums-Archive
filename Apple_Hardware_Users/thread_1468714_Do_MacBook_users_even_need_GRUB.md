---
title: "Do MacBook users even need GRUB?"
date: 2010-05-01
forum: Apple Hardware Users
---

### Post by xxander on 2010-05-01
Do MacBook users even need GRUB if we are dual-booting?  If I use rEFIt to boot into Ubuntu, do I need GRUB?  I can't figure out how to put the boot loader (GRUB) onto /dev/sd3.

---

### Post by kosumi68 on 2010-05-01
As you know, the Mac has EFI instead of BIOS. In order to boot "other PC operating systems", which assume there is a BIOS to talk to, the Mac EFI is equipped with a BIOS emulator, which boots the machine in the so-called "legacy" mode. This legacy mode is also used when booting the Ubuntu CDROM.

When installing Ubuntu, the grub-pc bootloader gets installed on the Ubuntu partition (this is where you have troubles, are you sure /dev/sda3 is your Ubuntu partition?), and the next time you reboot, the EFI emulates the BIOS which loads the grub-pc which boots Ubuntu. Pretty complicated, huh. To top it all off, the order in which the Mac EFI searches for bootable partitions usually leaves the legacy ones for last, resulting in loong boot times.

Since the refit program can be easily configured to boot the legacy partition first, it has become common for people to have it installed for that reason. (Also, back in the days of hardy heron, there was a problem with the partitioner in the installer which required a manual synchronization of the GPT boot record used by Apple and the MBR boot record used by Ubuntu, a process refit was able to do easily which saved many people at the time.)

So yes, we need grub, but we can do better:

In the best of worlds, we should be able to boot directly from efi, skipping all that bios emulation stuff. This is where the newly-developed grub-efi comes in. It is still in a development stage and still not for all machines and graphics cards, but it does improve the booting experience tremendously once set up and working properly.

With grub-efi as boot loader, when the Mac reboots, it will find an EFI-bootable partition named Ubuntu, load grub-efi and boot Ubuntu. That's it. And if you want to dual boot with OSX, just add OSX to your grub boot menu. Triple boot? no problem. Quad boot? sure. :-)

So yes, we need grub, but the grub-efi.

---

### Post by xxander on 2010-05-01
Wow, thank you for that very detailed response.  Sooo, since I need GRUB at the moment, do you know a way to fix my /dev/sd3 problem?

---

### Post by kosumi68 on 2010-05-01
> **xxander said:**
> Wow, thank you for that very detailed response.  Sooo, since I need GRUB at the moment, do you know a way to fix my /dev/sd3 problem?

A normal SATA driver has partition names sda1, sda2, sda3 etc. Are you missing an 'a'? :-)

---

### Post by xxander on 2010-05-01
I forgot to type the 'a'.. I meant /dev/sda3  sorry

---

### Post by kosumi68 on 2010-05-01
> **xxander said:**
> I forgot to type the 'a'.. I meant /dev/sda3  sorry

I thought so, but you never know. There was a post recently with a similar problem, and the question about bootcamp came up. Did you run bootcamp from OSX to allocate the space for Ubuntu? To know precisely what your disk looks like, please (from a terminal in OSX) post the output of
```

sudo fdisk -l

```

---

### Post by xxander on 2010-05-01
I did use Boot Camp for the space.  Then using gparted, I deleted it to make it unallocated.. I am kinda hesitant in using Terminal, so what will this do exactly?

---

