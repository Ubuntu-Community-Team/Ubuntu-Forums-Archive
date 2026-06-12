---
title: "installing ubuntu with dual boot camp"
date: 2008-09-10
forum: Apple Hardware Users
---

### Post by Jonathan45 on 2008-09-10
Hi.
im buying a mac and im just wondering if you can install Ubuntu/Kubuntu with dual boot camp without GRUB on a Mac and also use Ubuntu/Kubuntu on VMWare fusion?:popcorn:

---

### Post by cyberdork33 on 2008-09-10
> **Jonathan45 said:**
> Hi.
im buying a mac and im just wondering if you can install Ubuntu/Kubuntu with dual boot camp without GRUB on a Mac and also use Ubuntu/Kubuntu on VMWare fusion?:popcorn:

Ok, first lets nail down exactly what you are asking because you are using a bit of odd terminology. If by "dual boot camp" you just mean "dual boot" then...

Yes, you can Dual-boot you Mac with Ubuntu. You don't really *need* boot camp to do this, though, it can make partitioning easier.

No, you must have GRUB (or some other Linux bootloader) to load the Linux Kernel. This is true on _any_ PC, not just a Mac. You will not see GRUB unless you specifically choose to Boot Linux though.

Yes, You can also run Ubuntu in a VM (you can even run it inside either OS X or Ubuntu if you want), but if you mean you want to run the same Ubuntu install on your Hard Drive and in a VM in OS X, then that is a bit more difficult if not impossible.

Lastly, if you haven't already purchased VMWare Fusion, checkout [VirtualBox]("http://www.virtualbox.org/"). It is free and is almost as good.

---

### Post by Jonathan45 on 2008-09-10
Ok i meant the somewhat ugly black screen where you choose OS + i want to boot OS X as default not ubuntu (on my pc i had to choose Windows very fast due to a laggy screen)](*,)

---

### Post by cyberdork33 on 2008-09-10
> **Jonathan45 said:**
> Ok i meant the somewhat ugly black screen where you choose OS + i want to boot OS X as default not ubuntu (on my pc i had to choose Windows very fast due to a laggy screen)](*,)

Install rEFIt. You do not Boot OSX from GRUB, only Ubuntu.

---

### Post by Jonathan45 on 2008-09-10
ok do i hold down the alt-key to get the grub menu?:confused::confused::confused:

---

### Post by cyberdork33 on 2008-09-10
> **Jonathan45 said:**
> ok do i hold down the alt-key to get the grub menu?:confused::confused::confused:

not if you use refit.

You need refit anyway to fix the installer bug so install it for now, you can remove it later if you don't want it.

---

### Post by Jonathan45 on 2008-09-11
OK thanks

---

