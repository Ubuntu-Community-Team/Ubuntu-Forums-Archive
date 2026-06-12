---
title: "Dual-booting Ubuntu 12.04 and Linux From Scratch 7.5"
date: 2014-03-28
forum: Any Other OS
---

### Post by dclarion on 2014-03-28
I just built an LFS 7.5 system using Ubuntu 12.04 as the host system.  Not wanting to totally destroy my MBR, I ran update-grub from Ubuntu.  Trying to boot into LFS resulted in a kernel panic (VFS: Could not find root partition).  "Well," thought I, this uounds like a glitch in grub.cfig.  Examining said file, I saw:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux From Scratch (7.5) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root b75cb0c6-2ed8-4d68-9180-bca4e29e18cc
	linux /boot/vmlinuz-3.13.3-lfs-7.5 root=/dev/sda2
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

Since udev is in use and everybody else has a UUID in the "linux" line, I believe that I can safely assume that the device node in that line is my trouble spot.  The question is: how do I get the UUID into the "linux" line instead of the device node?  My understanding is that manually editing grub.cfg is contraindicated.

My thanks for any and all help.
DAC

---

