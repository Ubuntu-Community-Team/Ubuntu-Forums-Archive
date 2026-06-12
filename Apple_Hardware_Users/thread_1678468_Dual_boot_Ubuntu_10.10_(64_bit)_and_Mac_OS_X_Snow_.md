---
title: "Dual boot Ubuntu 10.10 (64 bit) and Mac OS X Snow leopard"
date: 2011-01-30
forum: Apple Hardware Users
---

### Post by rafamundez on 2011-01-30
I'm having issues dual booting Mac OS X and Ubuntu 10.10 64-bit .

The CD won't load the "Try it now" without installing feature as per the directions in:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)


So I used the 32 bit version of Ubuntu CD instead and it worked well to load the "Try it now" section to use GParted (after that, I used the 64 bit version to install it).  So then when I access GParted, I don't know how to make a 1 GB SWAP area.  How do I do that?

Also, no "Advanced" button showed up on the last dialog of the install (using the 64 bit version CD) so I couldn't "choose to install the boot loader (grub) to your root Ubuntu partition."  This led to there being 2 boot loaders, the rEFIt and the grub Ubuntu loader (which led to a crazy long amount of time to load up each boot.

Last but not least:
I'm wondering if a 64 bit version of Ubuntu is a good idea with the specs I have below and with the issues I'm currently having with the 64 bit.  Would it be better to go with the 32 bit? Will it have less issues than the 64 bit or will it be the same?



this is my Macbook Pro specs

Model Name:	MacBook Pro
Model Identifier:	MacBookPro5,5
Processor Name:	Intel Core 2 Duo
Processor Speed:	2.26 GHz
Number Of Processors:	1
Total Number Of Cores:	2
L2 Cache:	3 MB
Memory:	4 GB
Bus Speed:	1.07 GHz
Boot ROM Version:	MBP55.00AC.B03


THANKS!!!!

---

### Post by srs5694 on 2011-01-30
> **rafamundez said:**
> So I used the 32 bit version of Ubuntu CD instead and it worked well to load the "Try it now" section to use GParted (after that, I used the 64 bit version to install it).  So then when I access GParted, I don't know how to make a 1 GB SWAP area.  How do I do that?

In principle, you'd boot the live CD ("try it now" option) to launch GParted and resize a partition from there, since you can't resize any partition that's currently in use.

In practice, I advise against that. You've almost certainly got a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration, which is a minefield for mistakes made when modifying existing setups. Instead, I suggest you create a swap *file*. See [this page](https://help.ubuntu.com/community/SwapFaq) for directions. (I've just skimmed it, so I'm not positive how good it is; I found it with a quick Google.)

> Also, no "Advanced" button showed up on the last dialog of the install (using the 64 bit version CD) so I couldn't "choose to install the boot loader (grub) to your root Ubuntu partition."  This led to there being 2 boot loaders, the rEFIt and the grub Ubuntu loader (which led to a crazy long amount of time to load up each boot.

The delays may have more to do with BIOS emulation than anything else. This is one of many reasons I prefer to [boot Ubuntu using EFI](http://www.rodsbooks.com/ubuntu-efi/index.html) on Macs. It's a pain to set up this way, but you might want to consider it -- but only once you're comfortable with the basics.

> I'm wondering if a 64 bit version of Ubuntu is a good idea with the specs I have below and with the issues I'm currently having with the 64 bit.  Would it be better to go with the 32 bit? Will it have less issues than the 64 bit or will it be the same?

No, you've got plenty of RAM (64-bit tends to consume more RAM than 32-bit), and the issues you've mentioned have nothing to do with 64- vs. 32-bit installations. The only Mac-specific issues I'm aware of manifest only when booting with EFI, and those issues favor matching the OS's bitness to the EFI's. I'm guessing you've got a 64-bit EFI, since you've got a 64-bit CPU, but I'm not positive of that -- Apple might have released some systems with 64-bit CPUs and 32-bit EFIs, in which case you'd be better off with a 32-bit OS when booting in EFI mode.

---

### Post by rafamundez on 2011-01-30
Thanks for responding!!!

I want to try a clean install of everything again sometime soon--once I've determined exactly what I want I'm going to do.

So the first thing I'm going to do is get all the Snow leopard stuff out of the way.  Re-install everything there.  Then bootcamp the space for ubuntu  Then install rEFIt.

Now that I've got everything created, I want to create the SWAP space and format the bootcamp space I created above.  Is it OK for me to use my 32bit ubuntu disk for this?  Also, the link above only says how to create the SWAP space once ubuntu is installed, should I do that too? Or can I create that SWAP space prior to installing ubuntu? (assuming that formatting the bootcamp space to ext4 along with assigning it to be "root" (/) is easy)

Presumably at this point, I've either created the SWAP space or am putting it off until after I've installed ubuntu.  Now I go ahead and install either the 32 bit or 64 bit version of ubuntu (I'm definitely leaning towards 64 bit but I'm still not positive).

Now I'm wondering how to get rid of the extra boot loader; I already have rEFIt which is nice so I don't want the grub boot loader.  How do I get rid of that?

Last step: add swap space if its not already added.


Do you think all of that sounds good?



THANKS AGAIN!!!  ):P ):P ):P ):P

---

### Post by srs5694 on 2011-01-31
> **rafamundez said:**
> I want to try a clean install of everything again sometime soon--once I've determined exactly what I want I'm going to do.

So the first thing I'm going to do is get all the Snow leopard stuff out of the way.  Re-install everything there.  Then bootcamp the space for ubuntu  Then install rEFIt.

If you intend to re-install everything anyway, then you might want to experiment with the EFI-only boot method. It offers real advantages (and perhaps real disadvantages, depending on your system and specific needs). To do this you would *not* use Boot Camp, or you'd undo the ugly stuff it does with hybrid MBRs. (In terms of preparing disk space, there's nothing special about Boot Camp; it just facilitates repartitioning and creates a hybrid MBR.)

> Now that I've got everything created, I want to create the SWAP space and format the bootcamp space I created above.  Is it OK for me to use my 32bit ubuntu disk for this?  Also, the link above only says how to create the SWAP space once ubuntu is installed, should I do that too? Or can I create that SWAP space prior to installing ubuntu? (assuming that formatting the bootcamp space to ext4 along with assigning it to be "root" (/) is easy)

The link I provided relating to swap space describes how to create a swap *file*. This is acceptable, but if you're doing it from scratch you might as well create a swap *partition*. This is best done when creating partitions, and to create Linux partitions you really need to use Linux tools. You'd also do this before installation or from within the partitioning stage of the Ubuntu installation. Any generic guide on Ubuntu installation will tell you how to do this, although most such guides assume either an Ubuntu-only install or an Ubuntu/Windows dual boot.

If you want to prepare things ahead of time, it doesn't matter whether you use a 32- or 64-bit CD/DVD; the data structures are identical in either case.

> Now I'm wondering how to get rid of the extra boot loader; I already have rEFIt which is nice so I don't want the grub boot loader.  How do I get rid of that?

You don't. As far as I can tell, rEFIt cannot load Linux directly; you *must* have GRUB 2 (or conceivably some other boot loader) installed. That said, you can set GRUB 2's timeout value quite low so that you only see its menu for a second or two. The drawback to this is that you'll have a harder time selecting a non-Linux option from GRUB's menu if you need to do so.

---

### Post by djnichol66 on 2011-01-31
I used diskutil on Mac OS to partition my hard drive before installation according to the following instructions:

[http://montanalinux.org/mac-triple-boot.html](http://montanalinux.org/mac-triple-boot.html)

Worked for both my iMac7,1 and MacBookPro6,1.

Doug

---

