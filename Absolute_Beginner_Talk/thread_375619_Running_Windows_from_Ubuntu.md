---
title: "Running Windows from Ubuntu"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-03-04
Hi,
Is it true that one could run Win98 or xp form within Ubuntu without a dual boot?

---

### Post by chuckyp on 2007-03-04
yes there are many methods for accomplishing this.  I would suggest trying qemu with the kqemu module.   Would be the easiest virtualization i've found.  If you search the wiki there is an excellent article on getting the aforementioned running.  In fact I made a video demonstrating this in Fiesty because I was bored one night.  

[Video here]("http://www.youtube.com/watch?v=01OqyzEyV9M#GU5U2spHI_4")

---

### Post by Patrick K on 2007-03-04
QEMU doesn't support W98. You'll need VMServer.

---

### Post by gunthr on 2007-03-04
I use VMWare to run XP. It was a fairly easy setup and runs very smoothly.

---

### Post by chris062689 on 2007-03-04
I use VirutalBox, it's really quick and easy to setup, and I hear it's a lot faster than VMWare.

---

### Post by gunthr on 2007-03-04
It also looks like VirtualBox supports Vista. It's "experimental" in VMWare. The Vista installer failed repeatedly when I tried to install it, so I may have to check out VirtualBox myself.

The biggest downfall I see with VirtualBox is that, according to their website, USB support is only available in the enterprise version.

---

### Post by julian67 on 2007-03-04
Yes VirtualBox is incredibly good, seems to perform better than VMware and it's available as an open source GPL tarball or as no cost (for non commercial use) binaries with some extra features. You can build your own virtual machines with no difficulty and choose from dos, Windows 3.1 through to Vista, OS2, Linux 2.2 to 2.6 kernels, Netware, the BSDs, Solaris and L4 (whatever that is?????). I installed it on my openSuSE 10.2 laptop using the binary provided and there were no issues (make sure you meet the dependencies). There are also binaries available for Ubuntu 6.10 and 6.06. 

I've been able to make dsl-n and Ubuntu 6.10 virtual machines to play/learn with, they function really well.  There is a Windows installer too so Windows users can easily test out/use the various alternative Operating Systems without worrying about changing their system.

---

