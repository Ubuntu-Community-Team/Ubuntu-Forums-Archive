---
title: "Feisty (+ Beryl) + VMware Server with XP = slow"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Muppy on 2007-04-29
I have recently upgraded to Feisty and use VMware Server quite a lot. However, after installing version 1.0.2 or 1.0.3 (tried both versions) of VMware server and applying the vmware-any-any-update109 patch to get it running, it is HORRIBLY slow! Not only the VMware is slow, it also affects the whole Linux box. Every few seconds the whole system hangs (firefox, evolution, gnome-terminal, ... -- just everything), comes back again, hangs, comes back, hangs, ... Very weird! I didn't have that behaviour in Edgy. When I close the VMware, everything is fine. (Yes, I did install the latest VMware tools)

I have also tried virtualbox, installed an XP into it and a Visual Studio .NET 2003 (which is why I need the VMware). However, it seems that virtualbox does not deal with VS very well, I don't even get my programs compiled. VS completely hangs and has to be killed. So, this is not an alternative.

What can I do? 

My system spec:
Intel Core2Duo T5600
2GB RAM (VMware and/or virtualbox got 1GB of it)
...and the usual: CDROM, 250GB HDD, ATI graphics card, ASUS mobo

Does anyone have experience with QEmu? Does VS run in QEmu well? I actually wasted quite some time already trying different things (even VMware Workstation 5.5.3 -- same behaviour as VMware Server 1.0.2 or 1.0.3), I thought I better ask here...

Thanks,
Manfred

---

### Post by mejy on 2007-04-29
First off, you might want to try uninstalling vmware server and reinstalling from scratch, since the vmware kernel modules you're using could be incompatible with the feisty kernel.  This depends on how you installed vmware server, but a simple uninstall and reinstall should fix it.

The other point is that you're probably using a fairly old version of vmware server, and I've herd of incompatabilities with recent kernel releases in some older builds.  You could try either using the latest version on the vmware website, or using the vmware workstation beta builds until vmware server is updated to work correctly.

I've had similar issues with vmware server in Gentoo with the 2.6.20 kernels, so I think it's an upstream rather than Ubuntu issue.

Edit:  Check out [http://icanthack.com/?p=53]("http://icanthack.com/?p=53").

---

### Post by Muppy on 2007-04-29
Thanks for your quick reply! I have actually done all that already: cleaned out vmware totally from my system, got the latest tar-ball (version 1.0.3) from vmware's website, reinstalled it many times, always using the vmware-any-any-update109 patch to get the modules compiled. The result is still the same.

Maybe I just have to wait for vmware to fix this issue. I already assumed that this has something to do with the new kernel and not particularly with Ubuntu. However, since I couldn't find any clue on the Gentoo forums either (at home I use Gentoo, but without vmware, at work I use Ubuntu), I thought the ubuntuforums are the right place to ask this question... Maybe I should go to vmware's forums... ;-)

Thanks again!

Cheers,
Manfred

---

### Post by veloce on 2007-05-01
> **Muppy said:**
> I have recently upgraded to Feisty and use VMware Server quite a lot. However, after installing version 1.0.2 or 1.0.3 (tried both versions) of VMware server and applying the vmware-any-any-update109 patch to get it running, it is HORRIBLY slow! Not only the VMware is slow, it also affects the whole Linux box. Every few seconds the whole system hangs (firefox, evolution, gnome-terminal, ... -- just everything), comes back again, hangs, comes back, hangs, ... Very weird! I didn't have that behaviour in Edgy. When I close the VMware, everything is fine. (Yes, I did install the latest VMware tools)

I have also tried virtualbox, installed an XP into it and a Visual Studio .NET 2003 (which is why I need the VMware). However, it seems that virtualbox does not deal with VS very well, I don't even get my programs compiled. VS completely hangs and has to be killed. So, this is not an alternative.

What can I do? 

My system spec:
Intel Core2Duo T5600
2GB RAM (VMware and/or virtualbox got 1GB of it)
...and the usual: CDROM, 250GB HDD, ATI graphics card, ASUS mobo

Does anyone have experience with QEmu? Does VS run in QEmu well? I actually wasted quite some time already trying different things (even VMware Workstation 5.5.3 -- same behaviour as VMware Server 1.0.2 or 1.0.3), I thought I better ask here...

Thanks,
Manfred

Two things:
1. Make sure your vm is not setup as having two processors.  Yes, it works but it's just a bad idea.  The host uses the two processors better than the vm.

2. Forget using the vmware interface.  Instead, use rdp over host only virtual network.  It just works better and faster.

I have a similar system with just 1Gb ram and get better than native performance on my xp vms.

---

### Post by axm on 2007-11-17
[QUOTE=Muppy;2558160 Not only the VMware is slow, it also affects the whole Linux box. Every few seconds the whole system hangs (firefox, evolution, gnome-terminal, ... -- just everything), comes back again, hangs, comes back, hangs, ... Very weird! [/QUOTE]

Sounds like evms messing with your system, not vmware at all. You probably discovered that by now anyway, but just in case.

---

