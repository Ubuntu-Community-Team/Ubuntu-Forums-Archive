---
title: "Is the Arch kernel vanilla?"
date: 2008-10-23
forum: Arch and derivatives
---

### Post by handy on 2008-10-23
I think it is, I just need to verify it as what I have read has not used the word vanilla.

Thanks.

---

### Post by sub2007 on 2008-10-23
Technically yes as Arch (and Gentoo) use the term vanilla kernel to describe a kernel that is straight from package manager and is not custom compiled.

---

### Post by handy on 2008-10-23
So how does a vanilla kernel fit with the distro's that run custom kernels?

If Ubuntu was run on a custom kernel there would be required mods not compiled into it, what kinds of differences do they make when customizing a kernel for a distro?

The only kernel compiling I have done was when I was attempting to install Gentoo.  I had a hardware problem & ended up doing quite a few kernels before I finally gave up.

I suspect that each distro' has the modification that it makes to the vanilla kernel documented, & that someone could take a vanilla kernel & refer to this documentation to duplicate the kernel & of course customize it to suit their hardware/needs more fully.

---

### Post by Ayuthia on 2008-10-23
As far as I can tell, Ubuntu adds patches to the drivers and security updates.  Ubuntu keeps track of their info in launchpad.net ([https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux))and other distros do similar things.  Of course, Ubuntu also adds things like linux-restricted-modules, linux-ubuntu-modules, and linux-backport-modules too.  They contain things like proprietary drivers like the new Broadcom STA driver (linux-restricted-modules), the kernel module for open-source modules like ndiswrapper (linux-ubuntu-modules where ndiswrapper is open-source but the wireless drivers are proprietary, and changes made to included kernel modules (linux-backport-modules).

---

### Post by Majorix on 2008-10-23
I think it's edited. Because it asks you what you need support for (like booting from USB Devices and so on) during the initial installation.

---

### Post by fwojciec on 2008-10-23
It's not plain vanilla -- this is the [set of patches]("ftp://ftp.archlinux.org/other/kernel26/patch-2.6.27.1-1-ARCH.bz2") used for the current Arch kernel.

---

### Post by Ayuthia on 2008-10-23
> **fwojciec said:**
> It's not plain vanilla -- this is the [set of patches]("ftp://ftp.archlinux.org/other/kernel26/patch-2.6.27.1-1-ARCH.bz2") used for the current Arch kernel.

That is true.  This is from the What is Arch? wiki:
> Arch provides non-patched, vanilla software; packages are offered from pure upstream sources, how the author originally intended it be distributed. Patching only occurs in extremely rare cases, to prevent severe breakage in the instance of version mismatches that may occur within a rolling release model.

---

### Post by MisfitI38 on 2008-10-23
> **Majorix said:**
> .. it asks you what you need support for (like booting from USB Devices and so on) during the initial installation.

You are confusing the kernel with the initramfs. These questions are to configure your initramfs. The initramfs (initcpio) is provided simply to load drivers to boot the system.

---

### Post by Majorix on 2008-10-23
> **MisfitI38 said:**
> You are confusing the kernel with the initramfs. These questions are to configure your initramfs. The initramfs (initcpio) is provided simply to load drivers to boot the system.

Oh, I am sorry then. Thanks for clearing it up :)

---

### Post by handy on 2008-10-23
So from these responses it sounds as though the Arch kernel can be almost vanilla at worst & vanilla if there is no need to patch to avoid breakage?

---

### Post by Ayuthia on 2008-10-23
> **handy said:**
> So from these responses it sounds as though the Arch kernel can be almost vanilla at worst & vanilla if there is no need to patch to avoid breakage?

Based on their wiki it seems to be the case.  Also if you ever take a look at the time the kernel version is released and the time when the kernel gets updated, it does look like it is pretty vanilla.  It always seem that Arch releases a kernel release within a couple days of the actual kernel release.

EDIT: I take back what I just said.  I just saw that we are at 2.6.27.1 and kernel.org is now at 2.6.27.3.

---

### Post by crimesaucer on 2008-10-23
I know that the ABS PKGBUILD pulls the source of the vanilla kernel, and then it patches it with the -ARCH patch of the same package version.


I have only tried to build/compile the -ARCH kernel once. My experience with it was that for some reason when I tried to build a custom AMD64 kernel, with the -ARCH patch (using the make menuconfig command to configure the kernel settings), the end result was that it compiled as a generic x86_64 kernel like the binary version..... so I was confused why it didn't compile as an AMD64 kernel like I had chose in the menuconfig. 


All my other options that I chose were changed (so I know the menuconfig partially worked), like when I changed the timing from 300HZ to 1000HZ.


I also think the -ARCH patch does something special for resume/suspend..... because when I use a different kernel (like the zen2 or zenmm patched kernels), my computer will not resume or suspend properly..... everything else works perfectly.

---

### Post by disturbed1 on 2008-10-23
Arch's kernel has a ton of patches, it is far, far, far from vanilla . Quite a few of their packages also have minimal patches. Not nearly as hack happy as Ubuntu, but they are there.

The kernel patch file for 2.6.27 is 1.1mb in size containing 34,390 lines.

---

### Post by d_skillz on 2008-10-23
Very informative, thanks.

---

