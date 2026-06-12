---
title: "FATAL ERROR when installing"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by aalr1986 on 2008-02-08
I'm installing Kubuntu Gutsy Gibbon on my laptop. It's a DELL Vostro 1500, 2gb DDR667, core2duo 2.0ghz, NVIDIA GeForce 8600M 256mb (this is just in case my hardware has something to do with the error)

When I'm installing it, almost at the end of the installation it says that it "couldn't install GRUB on my hd0 partition. This is a fatal error."

I've never had this issue before.

What the heck is happening?!?!?!?

---

### Post by dstew on 2008-02-08
I have seen this bug reported before. The workaround was to format the filesystem as ext2. Then grub installs. Then, you can change the filesystem to ext3 later if you want.
EDIT: See the post by flying penguin in this thread:[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135)

---

