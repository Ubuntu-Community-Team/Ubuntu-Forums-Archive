---
title: "Can't install 12.10 on Early 2011 Macbook Pro"
date: 2012-11-16
forum: Apple Hardware Users
---

### Post by today33 on 2012-11-16
Hello,

When starting with a blank hard drive and Ubuntu 12.10 on a burned DVD, the install freezes. I booted with 'quiet' and 'splash' removed from the boot options and this line is the last:

fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver

It is the same problem mentioned in this bug:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/816689](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/816689)

I added modprobe.blacklist=radeon, and it booted to a low graphics mode that seems completely broken. I tried noapic and nomodeset kernel boot options to no avail.

Any ideas?

---

