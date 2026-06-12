---
title: "Question on boot record"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by rhomp2002 on 2007-04-15
I want to install another distro with a root, boot, swap and home partition and then add the distro to the GRUB for UBUNTU.  

Can I chain load it?

When I refer to the partition, do I refer to the root or the boot partition when I chain load it to the GRUB? or is there something else I need to do?

The last time I tried one of these I ended up losing the GRUB I already had and also lost one of the distros I had loaded.   Do not want to do that again.  That is the reason for the question.

I currently have XP, UBUNTU 6.10 and KUBUNTU 6.06 loaded and working well.  I want to add SABAYON to the mix just to see how it works and maybe later add another distro as well.  Would like to be able to delete the distro if I don't like it and keep it if I do.   Any help would be very much appreciated.   

I am having a great time playing with the various distros but I do want to keep a stable base version there and have the rest of the disk to play with (add distros, delete distros, etc).   I am trying to keep the GRUB as clean as I can and still do what I want with the disk.


:D :D :D

---

### Post by N Clement on 2007-04-15
There are a lot of tutorials you can find for grub if you google grub configure.  I will leave it to you to find one that you like.  You may also want to know that the grub configuration file is:

/boot/grub/menu.lst

---

### Post by BoneKracker on 2007-04-15
You can chainload it if you want.  If the other distro forces you to implement their bootloader, this is probably the best course of action.

If you chainload it:

When you install the other bootloader, make sure it is set up to write to the MBR of the boot or root partition you have set up for that distribution and not the MBR that you are using for ubuntu.  In other words, you will tell the grub on that new linux distro that the grub root is the partition on which the new linux kernel resides (it's root partition or boot partition if you have one).

To answer your question, you refer to partition which holds the contents of your /boot directory.  If you have a separate /boot partition you refer to that.  If you don't have a separate /boot partition, you refer to the "/" (root) partition.  If you use a separate boot partition, remember not to put "/boot" in the paths in menu.lst that indicate the location of the kernel.  (Actually, an easy way to avoid this is to put a symlink inside the /boot directory _to _the /boot directory -- that way, the path works with or without "/boot" in it whether or not you've got a separate partition.)

If you don't chainload it:

- Don't install the bootloader that comes with the other distribution.

- Create a soft symlink to the kernel that is generic (like vmlinux); that way, when you update the kernel, you just have to update the symlink, and not reboot into ubuntu and modify your bootloader configuration file.

Generally speaking, it's best to chainload them to keep things separated -- provided that you properly install each of the new GRUB instances such that it does not interfere with your existing ones by over-writing their MBRs.

But I'm curious if you've already got multiple linuxes on your system how you did it without already figuring all this out.

---

### Post by rhomp2002 on 2007-04-15
I didn't use the chain load for the current ones and the UBUNTU found the other Linux and the Windows.   The problem I had before I was not chain loading then either and it clobbered the GRUB with the other Linux (not UBUNTU or KUBUNTU).

What I want to end up with is a cleaned up GRUB for the main system and everything else chained to it.

---

### Post by BoneKracker on 2007-04-15
Just to be clear:

If you are "chainloading", what you're doing is telling your bootloader to call another bootloader (whatever booloader is located at the specified parition's MBR).

When you chainload Windows, you're calling it's bootloader.
To chainload another linux, you just create a similar entry in grub.conf (you don't have a bootline (an "image" section) for it.  The bootline goes in the grub.conf of the other distro.

So if you "chainload" another Linux distro, you do need to have grub (or some bootloader) installed on that Linux distro's partition.

The alternative, which is not chainloading, is to use a single bootloader and to create a bootline pointing to that Linux distro's kernel and informing it what partition to treat as "/" (and any other boot options).  In this second case, you should not use the bootloader of those alternative distro's.  (Well, they won't hurt anything as long as they don't over-write your main one, but it's redundant.)

---

### Post by rhomp2002 on 2007-04-15
Understood and thank you.

---

