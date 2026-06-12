---
title: "Bootable or not?"
date: 2009-03-28
forum: Apple Hardware Users
---

### Post by hilotime on 2009-03-28
20" intel imac (2006) white one
os leopard
owc 1T firewire 400 external

I realize this topic is discussed elsewhere, but not to my satisfaction I suppose. I have a problem for which I seek a simple solution, one explained, at least at this early stage of the game, in plain english. How can I install ubuntu on a partition of my external drive in a way that allows me to choose to boot from it rather than leopard, which is installed on my internal drive? Thank you in advance for your assistance in this matter.

---

### Post by cyberdork33 on 2009-03-28
> **hilotime said:**
> 20" intel imac (2006) white one
os leopard
owc 1T firewire 400 external

I realize this topic is discussed elsewhere, but not to my satisfaction I suppose. I have a problem for which I seek a simple solution, one explained, at least at this early stage of the game, in plain english. How can I install ubuntu on a partition of my external drive in a way that allows me to choose to boot from it rather than leopard, which is installed on my internal drive? Thank you in advance for your assistance in this matter.
You should try to identify your hardware with the machine's version string as shown here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

From your description you probably have an iMac5,1 (or one close to that). This hardware is pretty well supported.

Unfortunately, booting Ubuntu from an external hard drive is a little more complicated than a "normal" install. The Mac firmware is incapable of booting a "legacy OS" on an external drive through it's BIOS emulation (BootCamp). You can boot via EFI with grub-efi though, but this is still quite immature. Check the FAQ about this and you will be pointed to information.

---

