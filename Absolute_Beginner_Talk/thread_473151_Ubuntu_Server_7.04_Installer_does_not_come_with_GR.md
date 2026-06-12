---
title: "Ubuntu Server 7.04 Installer does not come with GRUB as option?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Akhran on 2007-06-13
For previous version of Ubuntu, I was able to install GRUB, and I think that was the default option. However, Ubuntu Server 7.04 doesn't seem to have GRUB as an option in the installer. Only option I see is "Install the LILO boot loader on a hard disk".

Is LILO the only option for 7.04 installer or did I miss out something?

Thanks!

---

### Post by confused57 on 2007-06-13
> **Akhran said:**
> For previous version of Ubuntu, I was able to install GRUB, and I think that was the default option. However, Ubuntu Server 7.04 doesn't seem to have GRUB as an option in the installer. Only option I see is "Install the LILO boot loader on a hard disk".

Is LILO the only option for 7.04 installer or did I miss out something?

Thanks!
No, grub is the default bootloader, unless you formatted your Ubuntu partition as  XFS filesystem, which requires using lilo.

---

### Post by Akhran on 2007-06-14
I reinstalled again just to make sure I have selected ext3 as the filesystem. I have installed LVM with two Volume Groups and two Logical Volumes, namely for / and swap. / is formated with ext3 filesystem. However, at the stage of installing boot loader, I was given only the option of LILO and where to install it, at the MBR or another partition. No mention of GRUB.

Any advice please?

Thanks.

> **confused57 said:**
> No, grub is the default bootloader, unless you formatted your Ubuntu partition as  XFS filesystem, which requires using lilo.

---

### Post by confused57 on 2007-06-14
> **Akhran said:**
> I reinstalled again just to make sure I have selected ext3 as the filesystem. I have installed LVM with two Volume Groups and two Logical Volumes, namely for / and swap. / is formated with ext3 filesystem. However, at the stage of installing boot loader, I was given only the option of LILO and where to install it, at the MBR or another partition. No mention of GRUB.

Any advice please?

Thanks.
This is pretty old, but found this concerning grub & LVM:
[https://bugs.launchpad.net/ubuntu/+source/partman-auto-lvm/+bug/21242](https://bugs.launchpad.net/ubuntu/+source/partman-auto-lvm/+bug/21242)

The way I read it, is that you might be able to create a separate /boot partition outside the LVM?

---

