---
title: "trouble with radeon framebuffer"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Fenotype on 2006-12-20
Hi everybody, I'm new to this forum.

Well, I'm having some troubles with loading the radeonfb module in the initial ramdisk.
I've tried the script proposed by evermind in
[http://ubuntuforums.org/archive/index.php/t-35035.html](http://ubuntuforums.org/archive/index.php/t-35035.html)
creating an initial ramdisk with mkinitrd and copying it in /boot/. It works well.

The problem is (well, I'm a little more than a newbie, so *I suppose* the problem is...) Dapper uses mkinitramfs instead of mkinitrd when creating the initrd by dpkg-reconfigure linux-image-*kernel_version*, and the method of putting evermind's script in /etc/mkinitramfs/scripts/ before reconfiguring the kernel doesn't works: I do not have a framebuffer as I desired.

So what can I do? Have I to load the script elsewhere rather than in /etc/mkinitramfs/scripts/ ..? Or the script only works with mkinitrd? :-k 

Many thanks, Fenotype

---

