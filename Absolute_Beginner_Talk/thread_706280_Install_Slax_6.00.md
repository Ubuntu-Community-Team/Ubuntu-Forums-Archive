---
title: "Install Slax 6.00"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-02-24
How do I install Slax 6.00 to my hdd from the LiveCD.
Keep in mind that im used to the simple Ubuntu Installation wizard :)

---

### Post by paultag on 2008-02-24
> **munch3 said:**
> How do I install Slax 6.00 to my hdd from the LiveCD.
Keep in mind that im used to the simple Ubuntu Installation wizard :)

There should be an option under the HDD installer for a USB install.
Cheers,
Tag

---

### Post by kagashe on 2008-03-02
I am presently running a sort of Frugal install of Slax 6.0.1 and posted the procedure on my [blog]("http://kagashe.blogspot.com/") and reproduced below:
> Today I downloaded the latest updated version Slax 6.0.1 which has fixed many bugs in Slax 6.0 which was launched on 13th Feb 2008.

I keep a spare 1 GB partition on my hard disc where I copy the iso and modify /boot/grub/menu.lst file to boot directly from the iso without burning CD.

First I create a "install_cd" directory in /tmp and mount the iso on it by the following commands:

    mkdir /tmp/install_cd
    mount slax-6.0.1.iso -o loop /tmp/install_cd

Then I copy the contents of the iso on /media/hda8 (hda8 is 1 GB partition formatted in ext3) by following command:

    cp -r /tmp/install_cd/* /media/hda8

Then I edit /boot/grub/menu.lst to add the following line:

    title Slax 6.0.1
    root (hd0,7)
    kernel /boot/vmlinuz root=/dev/ram ramdisk_size=1048576 rw changes=/dev/hda8
    initrd /boot/initrd.gz

"changes=/dev/hda8" is the cheatcode for saving configurations since Slax is a Live CD distribution which is loaded into RAM.

After rebooting I could run Slax.

After setting up the Network connection (Slax sets up automatically if it is dhcp but mine is static ip) I went to Slax site and downloaded Firefox module from this page.

After downloading I copied the module to /mnt/hda8/slax/modules so that it is available permanently.

Then I activated the module through Slax Module Manager. It is really very neat.

I have also changed time zone and added Hindi (IN) Keyboard and installed additional fonts through KDE Control Centre.

It is an excellent distribution and very fast since it runs from RAM.

---

