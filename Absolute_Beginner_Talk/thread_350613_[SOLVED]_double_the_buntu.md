---
title: "[SOLVED] double the buntu"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-01-31
I've got ubuntu running smooth and then I saw screenshots of Kubuntu. So, I decided that i'd try it too. After installing kubuntu in another partition grub doesn't look any different so I thought I was starting up Ubuntu but Kubuntu started instead. So they must look alike on the grub menu and now I can't get to Ubuntu. Is there a way to edit the menu to find both and to tell them apart?

---

### Post by p!=f on 2007-01-31
> **rusty4r said:**
> I've got ubuntu running smooth and then I saw screenshots of Kubuntu. So, I decided that i'd try it too. After installing kubuntu in another partition grub doesn't look any different so I thought I was starting up Ubuntu but Kubuntu started instead. So they must look alike on the grub menu and now I can't get to Ubuntu. Is there a way to edit the menu to find both and to tell them apart?
There's no need to have different installations for Ubuntu / Kubuntu / Xubuntu. Just install ubuntu-desktop / kubuntu-desktop / xubuntu-desktop packages in one installation and use all desktop environments as you like. :)

You need to edit /boot/grub/menu.lst and add an entry for your Ubuntu installation.
To answer your question I need you to post the output of the following command:
```

sudo fdisk -l

```

---

### Post by deadgobby on 2007-01-31
You may of not know this, you could of install KDE on Gnome. 
Here is a link
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

GObby

---

### Post by Sammi on 2007-01-31
There's only *one* Ubuntu, but several desktop enviroments. They can all be installed on the same Ubuntu installation, and you can then change between them in you GDM log in screen - not in GRUB.

---

### Post by rusty4r on 2007-01-31
Here is what I got

Disk /dev/hde: 20.0 GB, 20020396032 bytes
240 heads, 63 sectors/track, 2586 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1         524     3961408+   b  W95 FAT32
/dev/hde2             525        2586    15588720    f  W95 Ext'd (LBA)
/dev/hde5             525        2586    15588688+   7  HPFS/NTFS

Disk /dev/hdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1        2607    20940696   83  Linux
/dev/hdf2            2608        5134    20298127+  83  Linux
/dev/hdf3            5135        7684    20482875   83  Linux
/dev/hdf4            7685       19457    94566622+   5  Extended
/dev/hdf5            7685       10250    20611363+  83  Linux
/dev/hdf6           10251       12883    21149541    b  W95 FAT32
/dev/hdf7           12884       15329    19647463+   b  W95 FAT32
/dev/hdf8           15330       17913    20755948+   b  W95 FAT32
/dev/hdf9           17914       19321    11309728+   b  W95 FAT32
/dev/hdf10          19322       19457     1092388+  82  Linux swap / Solaris

---

### Post by rusty4r on 2007-01-31
And by the way I checked with the file browser they do both exist. Ubuntu is on hdf1 and kubuntu is on hdf2

---

### Post by rusty4r on 2007-01-31
> **p!=f said:**
> 

You need to edit /boot/grub/menu.lst and add an entry for your Ubuntu installation.

[/code]

I found the menu list if someone could talk me through editing it

---

### Post by orb9220 on 2007-01-31
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by pegazuz on 2007-01-31
> **Sammi said:**
> There's only *one* Ubuntu, but several desktop enviroments. They can all be installed on the same Ubuntu installation, and you can then change between them in you GDM log in screen - not in GRUB.

I am curious as why I could install Kubuntu on my external hard drive but Ubuntu wouldn't install despite several attempts since they are essentially the same. Right?  Now is it possible to run the Kubuntu as Ubuntu with some editing to change the desktop look?

---

### Post by p!=f on 2007-01-31
Quite nice list of partitions. Longer than expected. :)
> **rusty4r said:**
> And by the way I checked with the file browser they do both exist. Ubuntu is on hdf1 and kubuntu is on hdf2
Example:
Open your /boot/grub/menu.lst
(I suppose you'll be in Kubuntu)
```

sudo kate /boot/grub/menu.lst

```
Find lines which may look like this
> 
title           Debian GNU/Linux, kernel 2.6.20-5-lowlatency
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-5-lowlatency root=UUID=c787547d-40df-4c3a-8254-6dcb8ef5c34b ro vga=791 quiet splash 
initrd          /boot/initrd.img-2.6.20-5-lowlatency
boot

title           Debian GNU/Linux, kernel 2.6.20-5-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-5-generic root=UUID=c787547d-40df-4c3a-8254-6dcb8ef5c34b ro vga=791 quiet splash
initrd          /boot/initrd.img-2.6.20-5-generic
boot

Copy and paste before / after the block for Windows, edit the lines so it looks similar to this
> 
title           Debian GNU/Linux, kernel 2.6.20-5-lowlatency
root            (hd0,3) # you probably have (hd5,1) here
kernel          /boot/vmlinuz-2.6.20-5-lowlatency root=UUID=c787547d-40df-4c3a-8254-6dcb8ef5c34b ro vga=791 quiet splash 
initrd          /boot/initrd.img-2.6.20-5-lowlatency
boot

title           Debian GNU/Linux, kernel 2.6.20-5-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-5-generic root=UUID=c787547d-40df-4c3a-8254-6dcb8ef5c34b ro vga=791 quiet splash
initrd          /boot/initrd.img-2.6.20-5-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Debian GNU/Linux (Ubuntu), kernel 2.6.20-5-lowlatency
**root            (hd5,0)**
kernel          /boot/vmlinuz-2.6.20-5-lowlatency **root=/dev/hdf1** ro vga=791 quiet splash 
initrd          /boot/initrd.img-2.6.20-5-lowlatency
boot

title           Debian GNU/Linux (Ubuntu), kernel 2.6.20-5-generic
**root            (hd5,0)**
kernel          /boot/vmlinuz-2.6.20-5-generic **root=/dev/hdf1** ro vga=791 quiet splash
initrd          /boot/initrd.img-2.6.20-5-generic
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

(Only root and kernel root parameters should be changed, replace UUID with a device, to find UUID for your partition install vol_id package and run
```

sudo vol_id /dev/hdf1

```
but I'm not sure if it's same as if you'd run it from Ubuntu installation so try /dev/hdf1 first :)) Or you can just mount the second root partition and get the info from there.
I should note that you have grub in both installations. Remove grub in one of the installations (your pick :)) and edit menu.lst (if you removed it in Kubuntu. :)) If you run update-grub or if new kernel is installed in Ubuntu (it will run update-grub anyway), you'll end with the very same situation but unable to boot Kubuntu.
In your case the easiest would be to reinstall, create a seperate partition for /usr (like 5GB) and install k/ubuntu-desktop packages to have both desktops by hand. :)

---

### Post by p!=f on 2007-01-31
> **orb9220 said:**
> [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)
Will that make entries for both installations?

---

### Post by rusty4r on 2007-01-31
mine looks like this (the one in Kubuntu)


title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdf2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdf2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by rusty4r on 2007-01-31
> **orb9220 said:**
> [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

I was totally confused by the post in this link, but i did learn that theres really no sense in fixing it yet because when I install the updates grub will update.

---

