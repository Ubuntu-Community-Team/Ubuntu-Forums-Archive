---
title: "GRUB error 17"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by elmasto on 2008-02-16
hi,
I have a dual ubuntu/vista laptop, and I used GRUB to boot. It had been working just fine. As you might know, Vista has a recovery partition, which GRUB has been detecting as well. Yesterday, while logged in vista, I deleted the recovery partition because I was getting an external HDD for backup.
Now, my machine wound not reboot, and gets hung up at GRUB Error 17. I searched the the  forum and tried to modify the /boot/grub/menu.lst, but did not work. Here are the results
```

fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f21d957

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1259       18427   137909547+   7  HPFS/NTFS
/dev/sda2           18428       19410     7895947+  83  Linux
/dev/sda3           19411       19457      377527+   5  Extended
/dev/sda5           19411       19457      377496   82  Linux swap / Solaris


```
Before deleting the partition, the vista was about 131Gigs, Ubuntu 7Gigs and Recovery about 9 Gigs. I have only one harddrive.

And part of /boot/grub/menu.lst (that I grabbed using liveCD and mounting the linux partition

```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=88d01aea-6e36-4b00-a878-9ad6f55cd6e4 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=88d01aea-6e36-4b00-a878-9ad6f55cd6e4 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=88d01aea-6e36-4b00-a878-9ad6f55cd6e4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=88d01aea-6e36-4b00-a878-9ad6f55cd6e4 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title          Windows Vista/Longhorn (loader)
root           (hd0,1)
savedefault
makeactive
chainloader    +1


```

Please help me boot this. I have a lot of stuff, especially on the vista machine.
Thanks,

---

### Post by EXCiD3 on 2008-02-16
I'm not sure if this is causing your problem or not, but every time i had my external drive connected when i try to boot my computer gets Grub error 17. If you disconnect the drive then reconnect it after grub everything works fine. Also my ipod being connected does not allow my laptop to get past the BIOS for some reason. Its really weird. Hopefully this will help/

---

### Post by Berean on 2008-02-16
Don't worry!  You'll be able to access your Vista again.  If you place the Ubuntu CD into the drive and reboot, instead of re-installing Linux you can re-install the GRUB by looking at the options.  I'm new to this myself, but had the same problem, and all I did was exactly the aforementioned.  Vista will be safe, Ubuntu doesn't get changed and you get the option to boot either one.

---

### Post by Duck2006 on 2008-02-16
in your menu.lst linux and windoze are now pointing to the wrong partition
ie
in the windoze the root should be (hd0,0) not (hd0,1)
and in ubuntu the root should be (hd0,1) not (hd0,2)

from the live cd edit your menu.lst file and change these line and it should boot ok.

---

### Post by elmasto on 2008-02-16
I changed the lines above in menu.lst (i.e commented out one of the windows entries, and modified the other one to have (hd0,0) and replaces all of the ubuntu entries to have (hd0,1) ), however it is still giving be Error 17. Anything I have to do to make the changes take effect, or should that have been enough?

In trying to install it anew, I don't see an option just to re-install GRUB instead of replacing the entire ubuntu. Did I miss something? Thanks again.

---

### Post by Duck2006 on 2008-02-16
Have you tried super grub disk

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

you can reinstall and fix your grub problems from this disk.

---

### Post by dstew on 2008-02-16
I think I know the answer to this one. The error you are getting is a stage1.5 error, correct? That is, it just says Error 17, with no explanation. That is different from a stage2 error.

You are getting this error because when you installed grub, it was set up so that stage1.5 would get its stage2 from the 3rd partition. But when you deleted the first partition, now the third partition is your extended partition, and of course there is no stage2 there. The stage1.5 "get" is locked into the code of stage1.5 and you can't change it by editing the menu.lst. You have to re-install grub.

You can do that by using the supergrub disk, or you can just do it yourself with the Live CD. It is easy. First, boot the Live CD, open a terminal, and enter```
grub
```That gets you the grub command line, with the grub> prompt. At the grub prompt, enter```
root (hd0,1)
setup (hd0)
quit
```That corrects the stage1.5 error. But now, you have to correct the grub /boot/grub/menu.lst. The easiest way to do that is to enter your Ubuntu system by editing the root statement when the menu appears, so you will boot correctly. Press 'e' at the grub menu, select the root line, press 'e' again to edit it, and change the root to (hd0,1). Press enter to save the change, then 'b' to boot. Once inside Ubuntu, you can edit the /boot/grub/menu.lst file to make the root change permanent. Also, change the #groot (hd0,2) to (hd0,1) so when you get kernel updates the new kernel menu items will have the correct root statement. Finally, edit the Windows Vista root to be (hd0,0).

---

### Post by elmasto on 2008-02-16
Thanks folks,
I went ahead with a temporary solution. (Before reading the last post by dstew). I installed 7.04 on the unallocated partition that I had, and GRUB is working fine now, although I am a bit curious why it did not list 6.10 which is also on the machine. The next step is to consolidate the two linux partitions to one, but I think I am going to wait until I get my backup HDD before doing that :)

---

