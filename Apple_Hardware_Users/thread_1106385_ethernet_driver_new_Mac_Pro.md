---
title: "ethernet driver new Mac Pro"
date: 2009-03-25
forum: Apple Hardware Users
---

### Post by dinant on 2009-03-25
We just got a new mac pro (24 march 2009) and installed Ubuntu 8.10 on it. All works flawless, except ethernet driver. Any options?

---

### Post by cyberdork33 on 2009-03-25
can you identify the ethernet hardware?

(lspci output will help)

---

### Post by dinant on 2009-03-26
it states that it is Intel Corporation Device 10f6

---

### Post by runexe on 2009-03-27
I don't think I ended up posting about this - but I figured out how to get this to work - it's two lines that need to be added to the e1000e driver to recognize the new PCI ID (0x10F6) as a 82574 NIC. The folks on the e1000e mailing list already made a patch that's been accepted for inclusion in 2.6.30. In the meantime, I've taken to either building the module from source via the package at sf.net/projects/e1000, or from the kernel source and just adding the patch from:
[http://kerneltrap.org/mailarchive/linux-netdev/2009/3/25/5235664](http://kerneltrap.org/mailarchive/linux-netdev/2009/3/25/5235664)
Basically, in hw.h you add a line to
#define E1000_DEV_ID_82574LA			0x10F6
and in netdev.c:
{ PCI_VDEVICE(INTEL, E1000_DEV_ID_82574LA), board_82574 },
inside the pci_device_id e1000_pci_tbl[] structure.

I don't know if the Ubuntu Kernel folks will consider back-porting that patch to the Intrepid or Jaunty kernels.

---

### Post by cyberdork33 on 2009-03-27
> **runexe said:**
>  I don't know if the Ubuntu Kernel folks will consider back-porting that patch to the Intrepid or Jaunty kernels.
I'd file a bug in launchpad and request it. Especially since you have the fix.

---

### Post by runexe on 2009-03-27
> **cyberdork33 said:**
> I'd file a bug in launchpad and request it. Especially since you have the fix.

I'll see about doing that - thanks.

---

### Post by dinant on 2009-03-27
In the meanwhile I found a workaround by adjusting two files of the 0.5.18.3 standalone package from sf.net/projects/e1000 
Added the following to the netdev.c:
{ PCI_VDEVICE(INTEL, 0x10F6), board_82574}
and to hw.h
#define E1000_DEV_ID_82574L_NEW 0x10F6

then make install from directory src.

---

### Post by galexcd on 2009-03-30
> **runexe said:**
> I don't think I ended up posting about this - but I figured out how to get this to work - it's two lines that need to be added to the e1000e driver to recognize the new PCI ID (0x10F6) as a 82574 NIC. The folks on the e1000e mailing list already made a patch that's been accepted for inclusion in 2.6.30. In the meantime, I've taken to either building the module from source via the package at sf.net/projects/e1000, or from the kernel source and just adding the patch from:
[http://kerneltrap.org/mailarchive/linux-netdev/2009/3/25/5235664](http://kerneltrap.org/mailarchive/linux-netdev/2009/3/25/5235664)
Basically, in hw.h you add a line to
#define E1000_DEV_ID_82574LA			0x10F6
and in netdev.c:
{ PCI_VDEVICE(INTEL, E1000_DEV_ID_82574LA), board_82574 },
inside the pci_device_id e1000_pci_tbl[] structure.

I don't know if the Ubuntu Kernel folks will consider back-porting that patch to the Intrepid or Jaunty kernels.


Would you mind elaborating on how exactly I would do this?  I've got 8.10 running on my Mac Pro, and I am not getting any network at all over ethernet.

---

### Post by cyberdork33 on 2009-03-30
> **galexcd said:**
> Would you mind elaborating on how exactly I would do this?  I've got 8.10 running on my Mac Pro, and I am not getting any network at all over ethernet.
or if someone can create a deb package you can add it to the mactel-support ppa so that others can use it too...
[https://edge.launchpad.net/~mactel-support/+archive/ppa](https://edge.launchpad.net/~mactel-support/+archive/ppa)

---

### Post by galexcd on 2009-03-31
> **cyberdork33 said:**
> or if someone can create a deb package you can add it to the mactel-support ppa so that others can use it too...
[https://edge.launchpad.net/~mactel-support/+archive/ppa](https://edge.launchpad.net/~mactel-support/+archive/ppa)

That still isn't a major help to me who doesn't have a huge amount of experience with linux.  Maybe I'll try another distro, maybe fedora will actually be able to address my network card.

---

### Post by cyberdork33 on 2009-03-31
> **galexcd said:**
> That still isn't a major help to me who doesn't have a huge amount of experience with linux.  Maybe I'll try another distro, maybe fedora will actually be able to address my network card.

Yes, but this would be a documented item that needs to be installed until the proper fix is made in Linux proper. The PPA will not be much help anyway if you can't access the net.

This fix is something that hasn't been added to the Linux kernel yet, so any Linux distro is not going to support it unless they have patched it already themselves... and the way that you do that is file a bug explaining the problem and the fix and get the patch into the distribution. as you can see in the post here: 
[http://ubuntuforums.org/showpost.php?p=6966791&postcount=4](http://ubuntuforums.org/showpost.php?p=6966791&postcount=4)
the patch has been incorporated, it is just not yet part of the Ubuntu kernel (and likely not any kernel yet as the change was just barely made).

You have new hardware, the driver has to recognize the hardware before it can make it work. This is just normal process.

---

### Post by cyberdork33 on 2009-03-31
I made a bug report for this in launchpad:
[https://bugs.edge.launchpad.net/mactel-support/+bug/352414](https://bugs.edge.launchpad.net/mactel-support/+bug/352414)

If you are lucky, it will make it into Jaunty Final.

---

### Post by runexe on 2009-03-31
> **cyberdork33 said:**
> or if someone can create a deb package you can add it to the mactel-support ppa so that others can use it too...
[https://edge.launchpad.net/~mactel-support/+archive/ppa](https://edge.launchpad.net/~mactel-support/+archive/ppa)

 It's been a long time since I've played with making a deb package, but I'd be willing to do this. Right now I have the e1000-0.5.18.3 from sf.net patched, and it builds on my machine just fine. Since it's a kernel module I'm not sure what magic I need to do to make it work in general - e.g. I'm running Jaunty now, with kernel 2.6.28-11-server #38-Ubuntu. If anyone has experience/tips on how to package a kernel module - i.e. so people don't have to build it from source to install - that'd probably be nicer.

---

### Post by cyberdork33 on 2009-03-31
> **runexe said:**
> It's been a long time since I've played with making a deb package, but I'd be willing to do this. Right now I have the e1000-0.5.18.3 from sf.net patched, and it builds on my machine just fine. Since it's a kernel module I'm not sure what magic I need to do to make it work in general - e.g. I'm running Jaunty now, with kernel 2.6.28-11-server #38-Ubuntu. If anyone has experience/tips on how to package a kernel module - i.e. so people don't have to build it from source to install - that'd probably be nicer.
probably need to use dkms otherwise it will get superceeded everytime there is a kernel update. again, I don't know that it matters much about the PPA since you have to connect the machine in question to the net to get to it...

you can make a deb and post it here for people to download though. look into checkinstall. It should be able to make a deb file for you.

---

### Post by runexe on 2009-03-31
> **cyberdork33 said:**
> probably need to use dkms otherwise it will get superceeded everytime there is a kernel update. again, I don't know that it matters much about the PPA since you have to connect the machine in question to the net to get to it...

you can make a deb and post it here for people to download though. look into checkinstall. It should be able to make a deb file for you.

I wondered if I'd have to look at dkms. Thanks, I'll see if I can come up with something easily.

---

### Post by galexcd on 2009-04-29
Actually, thank you dinant for the solution, it worked.  I must have stupidly skipped your post the first time I was reading this thread.  The reason I couldn't figure out runexe's solution is because the link he provided has no place to download the e1000e package, however sf.net/projects/e1000 is the correct package.  After changing the appropriate lines and compiling the package, it worked instantly.

Once again, thank you for your help.

---

### Post by ipina on 2009-10-17
Hi, I confirm that the e1000e source package (1.0.15), downloaded from the link above, includes the patch for the Intel ethernet card, and it works fine (read the readme file in order to install!). Thanks to all you for your help.

---

