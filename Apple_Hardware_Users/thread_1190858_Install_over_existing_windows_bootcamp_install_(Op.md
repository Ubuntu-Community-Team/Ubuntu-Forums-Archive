---
title: "Install over existing windows bootcamp install (Operating System not found)"
date: 2009-06-18
forum: Apple Hardware Users
---

### Post by techknow on 2009-06-18
Hi,

I had an existing windows 7 install which I was hoping to replace with Ubuntu 9.04 so I tried to install it as follows

Installed rEfit from OS X (didn't check it had installed though)

I booted the LiveCD and using Gparted deleted the existing windows partition

Told the installer to use the largest existing free space left after deleting the partition

Told it to install grub to /dev/sda3 (the new partition)

After it installed I can boot and see two options when I press alt, exactly as I had when I used bootcamp but when I try and boot into the Windows one (now Ubuntu) I get an operating system not found error.

I burned rEfit to CD and tried to boot Linux using that but it just hangs on the penguin logo for ages. I also tried the partition tool to see if the partition tables needed synching which it said they didn't.

Any ideas, I'd really appreciate any advice

TechKnow

---

