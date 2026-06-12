---
title: "tripleboot and vmware/parallels"
date: 2007-11-12
forum: Apple Intel Users
---

### Post by beergut on 2007-11-12
I have searched the forum a bit couldn't find a definite answer to my question.

I have a Macbook Pro (CoreDuo), and running Leopard happily.

Ocasionally I use Windows XP, and Linux for different task.

I am running vmware fusion with XP and Ubuntu 7.1 on them. They ran pretty quickly.

However, I sometimes need to boot into the Os to use some very low level device for debugging embedded systems, so I thought triple boot might be an idea.

Has anyone did triple booting, AND also able to run them in VM under vmware/parallels under OSX (using native partition rather than virtual disk) ???

If so, can you shed some light on this issue ?

Thanks.

--
beergut

---

### Post by cyberdork33 on 2007-11-12
[http://communities.vmware.com/thread/104745](http://communities.vmware.com/thread/104745)

---

### Post by beergut on 2007-11-13
I have tried that, not very much help i am afraid.

I can deal with linux, but migrating a live system from virtual partion to real partition running bootcamp and vmware is not what I have confidence doing without some help.

---

### Post by cyberdork33 on 2007-11-13
> **beergut said:**
> I have tried that, not very much help i am afraid.

I can deal with linux, but migrating a live system from virtual partion to real partition running bootcamp and vmware is not what I have confidence doing without some help. That will be fairly tough. I would just make a copy of the files in your home partition and start from a fresh install. None of the VMs officially support booting linux from a real partition yet, just windows. I think the best place to get information is the forums for the VM you are looking to use as it is very specific. We tend to mainly support installing natively here (which you will still need to do), but getting it to work in a VM is another issue entirely.

There is also a [Virtualization Forum]("http://ubuntuforums.org/forumdisplay.php?f=308") here that might have better information.

---

