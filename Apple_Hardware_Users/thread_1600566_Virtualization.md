---
title: "Virtualization?"
date: 2010-10-19
forum: Apple Hardware Users
---

### Post by jonnny_j22 on 2010-10-19
Hi all,

Just been reading up a bit on virtualization; I know I'm late to the party, I just sort of dismissed it when it was first mentioned to me because it was in the same convo as cloud computing, and failed to grasp the security and multi task benefits.

Would someone mind confirming/busting some areas I'm still not clear on?

1) Is OS virtualization essentially like the games emulators that were so popular a few years ago (mario on your desktop, etc) so you could theoretically get any os - osx, wndows, solaris and run it unmodded on hardware it doesn't like - ppc, spark etc? Or does the original OS need to be compatible with your hardware? I read about osx emulators for pc's but they're both intel.

2) Does visualization effectively protect from malware, or it it best suited to protection from intruders? Surely malware would still save to the hdd and if confined by the virtulization, just wait for other programs to read it and spread it? Or have I missed something obvious?

3) what, if any is the difference between virtualizing an os and the teeny linux distros that run as a live cd from flash drives?

Thanks in advance guys!

---

### Post by AndyCee on 2010-10-19
> **jonnny_j22 said:**
> Hi all,

Just been reading up a bit on virtualization; I know I'm late to the party, I just sort of dismissed it when it was first mentioned to me because it was in the same convo as cloud computing, and failed to grasp the security and multi task benefits.

Would someone mind confirming/busting some areas I'm still not clear on?

1) Is OS virtualization essentially like the games emulators that were so popular a few years ago (mario on your desktop, etc) so you could theoretically get any os - osx, wndows, solaris and run it unmodded on hardware it doesn't like - ppc, spark etc? Or does the original OS need to be compatible with your hardware? I read about osx emulators for pc's but they're both intel.

2) Does visualization effectively protect from malware, or it it best suited to protection from intruders? Surely malware would still save to the hdd and if confined by the virtulization, just wait for other programs to read it and spread it? Or have I missed something obvious?

3) what, if any is the difference between virtualizing an os and the teeny linux distros that run as a live cd from flash drives?

Thanks in advance guys!

Interesting questions.
1. There are different kinds of virtualisation, and often the virtualised OS _does_ have certain requirements on the host it can run on. In my opinion, the simplest kind of OS virtualisation is the vmware/virtualbox kind. VirtualBox (for this example) is an application that runs on a host OS. You configure a VirtualBox Virtual Machine like a physical machine (memory, disk space, networking, graphics etc) and install a guest OS into a virtual disk. What is supported depends on the Virtualisation product. There are some products which can run a guest OS on a host of a different architecture, but it seems to be most common to run "like on like".

2. It depends on your setup. Generally a Guest OS has a filesystem (or most of the OS, at least) running seperately to the host. To the host, it looks like a blob that most host apps cannot access. If the guest is infected, it will only spread be able to spread to the host through shared resources (such as shared folders, shared processes etc) unless it is *really* clever malware.

3. OS Virtualisation is running an OS in a virtual machine within another OS on a physical machine. The portable usb linux's are full operating systems, booted from the USB disk.

There are different kinds of OS virtualisation, but virtual machines are the simplest to illustrate. Solaris has some interesting virtualisation options (zones, containers, logical domains) which all act slightly differently, depending on what you need.

---

### Post by jonnny_j22 on 2010-10-19
Thanks! really helped me get my head around it - I quite want to try this now! 

I found there are programs that run win xp on top of osx on ppc machines, but this seems a little over the top on resources for a 2003 emac! do you happen to know of any software for ppc linux that would do a similar thing? If it's possible I'd love to have a go at running freedos or even win 2000 on my g4 on top of a basic ubuntu mini.iso install?

---

### Post by srs5694 on 2010-10-19
[QEMU](http://wiki.qemu.org/Main_Page) is a virtualization package that includes CPU emulation, so you can (at least in theory) run Windows on a PowerPC Mac running Linux. I've never tried it for that, although I have run PowerPC Linux on an x86-64 Linux box using QEMU. Of course, there's a speed penalty for this sort of thing -- typically, software in the emulated environment runs at about 1/10 the speed it would if it were run natively. Thus, unless you're very patient, it's only good for running older software. I certainly wouldn't recommend running Windows 7 on your eMac under QEMU! Windows 98, or even Windows 2000, might be tolerable. Note that many more modern emulators, like VirtualBox, don't do full CPU emulation, and so are faster; but this also limits you to running like-CPU OSes, so you can't run Windows on a PowerPC Mac with this technology.

You might want to check out [Mac on Linux,](http://mac-on-linux.sourceforge.net) which enables you to run Mac OS (X or pre-X) under Linux, providing of course that you've got a PowerPC CPU. This is essentially the PowerPC Linux equivalent of VirtualBox.

---

