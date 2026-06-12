---
title: "VMWare under Gutsy - Fixed Speed"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by bubbalouie on 2007-09-19
I have been trying to get virtualisation running under gutsy for some work (I know alpha on production machine is bad).

I found Qemu to be a touch inflexible, and VirtualBox to be simply stunning, except the occasional freeze, though it would recover after a little while. After about 30 minutes of this VirtualBox was too much so I tried VMWare Player (Old Favorite).

Once I had compiled and configured all the needed bits everything worked.... Or so I thought, VMWare was blazingly fast, waaaay too fast. A minute would pass every 20 seconds! Double clicking is impossible in this state along with half a dozen other tasks. A little research turned up the following work around:

Update /boot/grub/menu.lst to have the following new **Bold** section:

> ## ## End Default Options ##

title           Ubuntu, kernel 2.6.22-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=552164d6-9db8-477c-a3c9-27348edd500d ro quiet splash **clock=pit**
initrd          /boot/initrd.img-2.6.22-10-generic
quiet

title           Ubuntu, kernel 2.6.22-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=552164d6-9db8-477c-a3c9-27348edd500d ro single
initrd          /boot/initrd.img-2.6.22-10-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Time keeping is not perfect, but VERY usable, if you tell VMWare tools too sync the guests time with the host everything runs beautifully.

I don't know if this is a kernel bug or not, but I suspect it may also explain the 'freezing' in VirtualBox.

For more info:

[http://www.vmware.com/pdf/vmware_timekeeping.pdf](http://www.vmware.com/pdf/vmware_timekeeping.pdf)

---

