---
title: "Setting up VirtualBox/Parallels"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by WillJeffery on 2008-06-13
So I have Hardy working great when I boot into it, but ideally I'd like use OS X and Ubuntu at the same time.

I have both Parallels and VirtualBox installed, but I don't know how to select my Ubuntu partition as the boot image. Halp pls?

TYVM in advance!

---

### Post by cyberdork33 on 2008-06-13
you'll have to ask about that in the particular VM's support areas since it is dependent on the software's configuration.

---

### Post by mfox on 2008-06-14
I'm not sure what you mean by select Ubuntu partition as your boot image.  When you install a virtual machine (either Parallels or VirtualBox), you set it up through that software and there is no partition to deal with.  The virtual machine makes its own pseudo-partition and that's all it sees. It's not like a dual boot system where you have to choose an OS to boot up at the outset.  Once it's set up, you start this through the virtual software, which lists your virtual machines at startup and asks which one you want to boot up.

Perhaps I'm misunderstanding your question - could you be referring to setting up Ubuntu as a virtual machine?  I have Ubuntu 8.04 running on both Parallels and VirtualBox.  The former has a problem with the Parallels Tools (mouse right-click and scroll wheel do not work; Parallels is aware and is working on a fix), at least on the 8.04 version. So if you want 8.04 I would recommend using VirtualBox. Ubuntu 7.10 works fine on Parallels.

---

### Post by cyberdork33 on 2008-06-14
he is talking about using a real partition for his VM. Fusion can do this with some trickery, VirtualBox does not support this (yet).

---

