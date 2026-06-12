---
title: "Which virtualization? kvm vs vmware? virtualbox?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by NoTiG on 2007-04-17
im looking for something so that i can run native windows apps (mainly MSN, and shockwave plugin ) seamlessly integrated. i have an athlon dualcore x2 4200... and 2 GB of ram. 

im leaning towards KVM since its integrated in the kernel and seems the easiest to get going. what do you think?

---

### Post by bluenova on 2007-04-17
I've found the easiest to use is virtualbox, and it run much quicker than vmware, but it's still quite new so can be a bit buggy.

---

### Post by MystaMax on 2007-04-18
I don't know much about KVM solutions. How are they managed? How are guest OSes installed and managed. I'm just not sure how all that works together. But, I found this info at desktoplinux.com:
[quote=desktoplinux.com]
On x86 systems with the Intel VT or AMD-V extensions, Ubuntu supports the new KVM (Kernel-based Virtual Machine support) virtualization, which was first implemented in the Linux 2.60.20 kernel. This enables users to run multiple virtual machines on unmodified Linux. Each virtual machine has private virtualized hardware: a network card, disk, graphics adapter and so on. Canonical Ltd. officials said Ubuntu is the first Linux distribution that supports VMware's VMI (Virtual Machine Interface), which provides optimized performance under VMware.
[/quote]

**edit:** Ok found some more info, basically answering my own question over @ [http://kvm.qumranet.com/kvmwiki/FAQ](http://kvm.qumranet.com/kvmwiki/FAQ)

In what aspects would you say virtualbox is quicker than vmware?. Personally, I found vmware harder to upgrade then to install. If I'm not mistaken the installer for vmware isn't bad (although its completely on the CLI). VirtualBox looks interesting, and if its easy to install and runs WinXP/Vista smooth enough for testing, then I may make the switch. 

I'm going to test VirtualBox once Fiesty is released, as I'll be rebuilding my laptop.

**edit:** I also found some instructions on how to install VirtualBox for those interested here: [http://ubuntuforums.org/showthread.php?t=340113&highlight=VirtualBox](http://ubuntuforums.org/showthread.php?t=340113&highlight=VirtualBox)

---

