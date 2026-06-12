---
title: "March Linux 2.0 installation on hard drive."
date: 2008-11-13
forum: Arch and derivatives
---

### Post by kagashe on 2008-11-13
March Linux 2.0 is based on Arch Linux with openbox, pcmanfm, lxpanel, lxappearance etc. The developer has built a Live CD using Linux Live scripts and SLAX kernel. [Beta1 iso]("http://downloads.tuxfamily.org/marchlive/MarchLinux2.0/MarchLinux2.0-beta-1.iso") of the Live CD is available [here]("http://downloads.tuxfamily.org/marchlive/MarchLinux2.0/") for testing.

I tried the Live CD and liked it. Although, installation is not possible directly from Live CD, the developer started writing a [procedure]("http://marchlinux.tuxfamily.org/wiki/index.php?n=Main.DirtyInstallation") on its [wiki]("http://marchlinux.tuxfamily.org/wiki/").

I tried to install but it failed at Kernel installation stage at Step 6. The developer advised to use [this procedure]("http://wiki.archlinux.org/index.php/Install_Arch_from_within_another_distro#Prepare_System") on ArchWiki. I had to create /proc /sys /dev directories before starting the ArchWiki procedure, which was required only for kernel installation. All the packages were already available on the hard disc through Step 4 (Unsquashing modules) of March Linux wiki page.

Grub could not be installed properly but I could boot the system after adding following lines to existing /boot/grub/menu.lst

    title Marchlinux (on /dev/sda3)
    root (hd0,2)
    kernel /boot/vmlinuz26 root=/dev/sda3 ro
    initrd /boot/kernel26.img

    title Marchlinux (on /dev/sda3) fallback
    root (hd0,2)
    kernel /boot/vmlinuz26 root=/dev/sda3 ro
    initrd /boot/kernel26-fallback.img

Before booting I created /etc/fstab and configured /etc/rc.conf file.

I could run the installed system on the hard drive. I created a user before starting X.

Since it is based on Arch Linux I could upgrade to the latest packages on Arch through pacman. There was an error during upgrade and I had to remove a symlink /usr/lib/klibc/include/asm

I am very happy to use this variant of Arch.

kagashe

---

### Post by Sorivenul on 2008-11-13
Awesome!  
I'm glad there is at least some way to get March installed.  The methods one had to use to get 1.0 to HD were nightmarish at best.  I'll have to give it a try again.

---

### Post by kagashe on 2008-11-13
> **Sorivenul said:**
> Awesome!  
I'm glad there is at least some way to get March installed.  The methods one had to use to get 1.0 to HD were nightmarish at best.  I'll have to give it a try again.Why 1.0, download March 2.0 and install. I am here to help.

kagashe

---

### Post by Sorivenul on 2008-11-13
> **kagashe said:**
> Why 1.0, download March 2.0 and install. I am here to help.

kagashe

My mistake for using incorrect wording.
I was trying to say a harddrive install of 1.0 was a nightmare, I'll have to try 2.0.  If I have any issues, I'll come to you kagashe.

---

### Post by kagashe on 2008-11-15
I added standalone Compiz Fusion with lxpanel. Here is a screenshot.

kagashe

---

