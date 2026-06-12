---
title: "I can't understand what problem is happenig."
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by flight-jet on 2006-08-01
Hello everyone.
I New to enter "ubuntu" world.
I am using Performa7600,and I tried to install ubuntu.
I could undersrand untill using BootX method,but after rebooting,it occured kernel panic.:confused: 

It seems like due to using Realtek8139 card.

Never reboot:x 

Please someone,if you can,please teach me that are there problem on installing to OldWorld Machine?

Thanks
-------------------
IRC = sora_umi

---

### Post by avtolle on 2006-08-01
[http://ubuntuforums.org/showthread.php?t=224369&highlight=world+Mac](http://ubuntuforums.org/showthread.php?t=224369&highlight=world+Mac) is a recent thread, which you may not have seen, dealing with the Old World Mac issue. The final few posts may be very helpful. Please, if you have seen this, let me know, so I can try to find other threads. By the way, you might want to consider posting in the MacIntoshh/Apple/PPC/Intel forum where more experienced eyes may see your post and provide help with your Old World Mac problem.

---

### Post by flight-jet on 2006-08-02
Thank you for replying,Avtolle.
I thought the problem is ethercard.](*,) 
When a booting process,at point that reading ethercard,kernel said like below.

Begin: Loading modules ...
[   67.612771] NET: Registered protocol family 1
[   68.353528] 8139cp 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
**[   68.373433] 8139cp pci dev 0000:00:0f.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip**
[   68.393045] 8139cp Try the "8139too" driver instead.
[   68.440456] 8139too Fast Ethernet driver 0.9.27
[   68.460393] PCI: Enabling device 0000:00:0f.0 (0004 -> 0007)
[   68.480823] eth0: RealTek RTL8139 at 0x400, 00:06:7b:04:da:**,IRQ 25
Done.
Begin: Initializing /dev ...
Done.
Begin: Mounting root file system ...
Begin: Running /scripts/local-top ...
Done.
ALERT! /dev/sda6 does not exist.Dropping to a shell!
:confused: 
.....
---------
That is the problem of my PowerMachintosh 7600/132 Machine.

I did all the things that described in "Install Prpcess".
I coppied "vmlinux" to /hfs/System Folder/Linux Kernels,and did "initrd.img" to hfs/System Folder.

When a installing process,there was no problem,but when a rebooting time,caused a problem above.](*,) 

So I gived up to Install Ubuntu5.10,I tried gentoo linux,but same problem occured.
gentoo did't recognize ethercard,too.

I used modprobe,and selected "8139too" module,but couldn't lead.:confused: 

Not supported card?

I can't do nothing.
Please help me!

---

