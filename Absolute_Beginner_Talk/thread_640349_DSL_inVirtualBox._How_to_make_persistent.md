---
title: "DSL inVirtualBox. How to make persistent?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by ayenack on 2007-12-14
Hello all. I've been experimenting with Damn Small Linux in a VM (Virtual Box) on Ubuntu 7.10 and am trying to make it persistent. Not to hard to do when using DSL on USB stick but can't for the life of me work out how to do it inside the VM, any ideas?

What I've tried so far.
1. Installing to hda1/2 etc.
2. Installing to sda1/2 etc.
3. Making new Hard Drive for DSL inside Virtual Box and trying to install to that.
4. Assigning new hard drive to the DSL VM install from virtual box Hard Drive preferences.
5. Frugal Install.
7. HD install.
8. Installing to /mydsl/home etc.

And all kinds of variants on the theme. The problem is the way Virtual Box assigns its hard drive tables I think. Apparently this can be done I just can't work out how.:(

The way I'm getting round this at the moment is to take a snapshot of the VM and use that. Solves the problem but I want to work this one out if possible. So if anyone has managed to do this please tell me how! ;)

Thanks.

Tutorial welcome. Thanks again.

---

### Post by hyper_ch on 2007-12-14
how about trying it with vmware instead of vb?

(And maybe it's better to ask in the DSL forums as people there probably know it better than we do here)

---

### Post by ayenack on 2007-12-14
Much easier to do in vmware but vmware runs slow on my box unfortunately where as Virtual Box runs very well, don't ask me why.;)

Thanks though.

---

### Post by virtualXTC on 2008-03-01
You need to partition the new (virtual) drive.  Creating a new drive in VIrtualBox simply creates the disk (hda),  Once you create a partition, you will be able to install to hda1.

When you start VIrtualBox from your Damn Small Linux CD or iso at the boot prompt type:

```
boot: install
```


choose option "10. Partition Tool cfdisk"

use disk hda (provided you want to use your first mounted virtual disk)

Create a bootable linux partition, write it, then quit.

You are now free to choose one of the installation methods.

good luck!

---

### Post by virtualXTC on 2008-03-01
You need to partition the new (virtual) drive.  Creating a new drive in VIrtualBox simply creates the disk (hda),  Once you create a partition, you will be able to install to hda1.

When you start VIrtualBox from your Damn Small Linux CD or iso at the boot prompt type "install":

```
boot: install
```


choose option "10. Partition Tool cfdisk"

use disk hda (provided you want to use your first mounted virtual disk)

Create a bootable linux partition, write it, then quit.

You are now free to choose one of the installation methods.

good luck!

---

