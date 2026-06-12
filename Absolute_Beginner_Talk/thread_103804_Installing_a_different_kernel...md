---
title: "Installing a different kernel.."
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Kindred on 2005-12-14
Hi,

Someone recommended I install a 686 kernel to fix a hardware problem I am having (no drivers), I currently am using the default breezy install for amd64.  

I'm just wondering, if I did this would anything break?  Current software/hardware etc?  Would my system then be in 32bit mode?

I'm hesitant to try it because i'm not sure of the consequences.

Any help would be great, thanks.

---

### Post by Sutekh on 2005-12-14
Having problems with drivers?  What sort of problems?  As far as I know, and I could be wrong, issues with drivers (in 64-bit Ubuntu) are to do with the 64-bit operating system libraries and such, not the kernel type.  

That being the case, you may need to install the i386 (32-bit) version of Ubuntu to fix these issues.  This means a new installation.  

You can run a 32-bit chroot environment *inside* your 64-bit installtion, meaning you can run 32-bit stuff in the 64-bit installation, but I have no knowledge in doing this.

As for the kernel... What is your processor type?

---

